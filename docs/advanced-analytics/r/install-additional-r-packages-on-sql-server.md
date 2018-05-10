---
title: Installare i nuovi pacchetti di R in servizi di SQL Server Machine Learning | Documenti Microsoft
description: Aggiungere i nuovi pacchetti R per SQL Server 2016 R Services o SQL Server 2017 Machine Learning Services (In-Database)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/08/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 57c5d4b9c3584a4aa556b1f4b6f7541a14f91a00
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="install-new-r-packages-on-sql-server"></a>Installare i nuovi pacchetti di R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come installare i nuovi pacchetti di R a un'istanza di SQL Server in cui è abilitato l'apprendimento.

Sono disponibili più metodi per l'installazione di nuovi pacchetti di R, a seconda di quale versione di SQL Server è che se il server abbia accesso a internet.

+ [Installare i nuovi pacchetti utilizzando gli strumenti di R, con accesso a internet](#bkmk_rInstall)

    Usare i comandi di R convenzionali per installare i pacchetti da Internet. Questo è il metodo più semplice, ma richiede accesso amministrativo.

    **Si applica a:**[!INCLUDE[sssql15-md](../../includes/sssql15-md.md)][!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]. Occorre inoltre per le istanze di [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] in Gestione dei pacchetti tramite DDL non è stata attivata.

+ [Installare i nuovi pacchetti di R in un server con **non** l'accesso a internet](#bkmk_offlineInstall)

    Se il server non ha accesso a internet, sono necessari alcuni passaggi aggiuntivi per preparare i pacchetti. In questa sezione viene descritto come preparare i file necessari per l'installazione del pacchetto e le relative dipendenze.

+ [Installare i pacchetti utilizzando l'istruzione CREATE libreria esterna](#bkmk_createlibrary) 

    Il [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) informativa è disponibile in SQL Server 2017, affinché sia possibile creare una libreria di pacchetto senza esecuzione di R o Python code direttamente. Tuttavia, questo metodo richiede preparare in anticipo tutti i pacchetti richiesti e richiede le autorizzazioni di database aggiuntive.

    **Si applica a:** [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]; restrizioni

## <a name="bkmk_rInstall"></a> Installare i nuovi pacchetti R tramite Internet

È possibile utilizzare gli strumenti standard di R per installare i nuovi pacchetti in un'istanza di SQL Server 2016 o SQL Server 2017. Questo processo richiede che sei un amministratore nel computer.

> [!IMPORTANT] 
> Assicurarsi di installare i pacchetti per la libreria predefinita associata con l'istanza corrente. Non installare mai pacchetti in una directory dell'utente.

Questa procedura viene descritto come installare pacchetti utilizzando RGui; Tuttavia, è possibile utilizzare RTerm o qualsiasi altro R della riga di comando strumento che supporta l'accesso con privilegi elevato.

### <a name="install-a-package-using-rgui-or-rterm"></a>Installare un pacchetto utilizzando RGui o RTerm

1. Passare alla cartella sul server in cui sono installate le librerie di R per l'istanza.

  **Istanza predefinita**

    SQL Server 2017: `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

  **Istanza denominata**

    SQL Server 2017: `C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

  Se è stata utilizzata l'associazione per l'aggiornamento di machine learning componenti, il percorso potrebbe essere modificato. Verificare sempre il percorso dell'istanza prima di installare i nuovi pacchetti. 

2. RGui.exe e scegliere **Esegui come amministratore**.

    Se non si dispone delle autorizzazioni necessarie, contattare l'amministratore del database e fornire un elenco dei pacchetti che è necessario.

3. Dalla riga di comando, se si conosce il nome del pacchetto, è possibile digitare: `install.packages("the_package-name")` tra virgolette sono necessarie per il nome del pacchetto.

4. Quando viene richiesto un sito mirror, è possibile selezionare qualsiasi sito a cui è utile per il percorso.

5. Se il pacchetto di destinazione dipende da pacchetti aggiuntivi, il programma di installazione di R automaticamente le dipendenze vengono scaricate e li installa automaticamente.

6. Per ogni istanza in cui è necessario utilizzare il pacchetto di installazione separatamente. Pacchetti non possono essere condivisa tra più istanze.

## <a name = "bkmk_offlineInstall"></a> Installazione offline utilizzando gli strumenti di R

Per installare pacchetti R in un server che non dispone dell'accesso a internet, è necessario:

+ Analizzare le dipendenze in anticipo.
+ Scaricare il pacchetto di destinazione in un computer con accesso a Internet.
+ Scaricare tutti i pacchetti necessari nello stesso computer e inserire tutti i pacchetti in un archivio singolo pacchetto.
+ Codice postale archivio se non è già in formato compresso.
+ Copiare l'archivio di pacchetto in un percorso sul server.
+ Installare il pacchetto di destinazione, specificando il file di archivio come origine.

> [!IMPORTANT] 
> > Verificare che per analizzare tutte le dipendenze e scaricare **tutti** necessari pacchetti **prima** iniziare l'installazione. È consigliabile [miniCRAN](https://mran.microsoft.com/package/miniCRAN) per questo processo. Il pacchetto R accetta un elenco di pacchetti da installare, consente di analizzare le dipendenze e ottiene tutti i file compressi automaticamente. miniCRAN crea quindi un singolo archivio che è possibile copiare nel computer server.
> 
> Per informazioni dettagliate, vedere [creare un repository di pacchetti locali tramite miniCRAN](create-a-local-package-repository-using-minicran.md)

Questa procedura si presuppone che sia stato preparato tutti i pacchetti necessari, in formato compresso e sono pronti per copiarli nel server.

1. Copia il pacchetto compresso file o per più pacchetti, il repository completo che contiene tutti i pacchetti compressi formato, in una posizione che il server può accedere.

2. Aprire la cartella nel server in cui sono installate le librerie di R per l'istanza. Ad esempio, se si utilizza il prompt dei comandi di Windows, passare alla directory in cui si trovano RTerm.Exe o RGui.exe.

  **Istanza predefinita**

    SQL Server 2017: `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`

  **Istanza denominata**

    SQL Server 2017: `C:\Program files\MSSQL14.<instanceName>\R_SERVICES\bin\x64`
    
    SQL Server 2016: `C:\Program files\MSSQL13.<instanceName>\R_SERVICES\bin\x64`

3. Fare clic su di RGui o il prompt dei comandi e selezionare **Esegui come amministratore**.

4. Eseguire il comando di R `install.packages` e specificare il pacchetto o nome di repository e il percorso del file ZIP.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Questo comando consente di estrarre il pacchetto R `mynewpackage` dal file compresso locale, presupponendo che la copia è stato salvato nella directory `C:\Temp\Downloaded packages`, quindi installa il pacchetto nel computer locale. Se il pacchetto contiene tutte le dipendenze, il programma di installazione verifica i pacchetti esistenti nella libreria. Se è stato creato un repository che include le dipendenze, il programma di installazione installa anche i pacchetti richiesti.

    Se tutti i pacchetti necessari non sono presenti nella libreria di istanza e non possono essere disponibile nei file compressi, l'installazione del pacchetto di destinazione non riesce.

## <a name="bkmk_createlibrary"></a> Utilizzare un'istruzione DDL per installare un pacchetto 

In SQL Server 2017, è possibile utilizzare il [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione per aggiungere un pacchetto o un set di pacchetti a un'istanza o un database specifico. L'istruzione DDL e i ruoli di database di supporto sono progettati per semplificare l'installazione e la gestione dei pacchetti da un proprietario del database senza dover ricorrere a strumenti di R o Python.

Questo processo richiede alcune attività di preparazione, rispetto all'installazione dei pacchetti utilizzando metodi R o Python convenzionali.

+ Tutti i pacchetti devono essere disponibili come file compresso locale, anziché il download da internet.

    Se non si dispone dell'accesso al file system nel server, è inoltre possibile passare un pacchetto completo come una variabile, utilizzando un formato binario. Per ulteriori informazioni, vedere [creare libreria esterna](../../t-sql/statements/create-external-library-transact-sql.md).

+ L'istruzione ha esito negativo se i pacchetti richiesti non sono disponibili. È necessario analizzare le dipendenze del pacchetto che si desidera installare e assicurarsi che i pacchetti vengono caricati per il server e il database. Si consiglia di utilizzare **miniCRAN** o **igraph** per l'analisi delle dipendenze di pacchetti.

+ È necessario disporre delle autorizzazioni necessarie nel database. Per informazioni dettagliate, vedere [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

### <a name="prepare-the-packages-in-archive-format"></a>Preparare i pacchetti in formato di archiviazione

1. Se si sta installando un singolo pacchetto, è possibile scaricare il pacchetto in formato compresso. 

2. Se il pacchetto richiede eventuali altri pacchetti, è necessario verificare che i pacchetti richiesti siano disponibili. È possibile utilizzare miniCRAN per analizzare il pacchetto di destinazione e identificare tutte le relative dipendenze. 

3. Copiare il file ZIP o miniCRAN repository che contiene tutti i pacchetti in una cartella locale nel server.

4. Aprire un **Query** finestra, utilizzando un account con privilegi amministrativi.

5. Eseguire l'istruzione T-SQL `CREATE EXTERNAL LIBRARY` per caricare la raccolta di pacchetto compresso nel database.

    Ad esempio, l'istruzione seguente nomi, come origine del pacchetto, di un repository miniCRAN contenenti il **randomForest** pacchetto, insieme alle relative dipendenze. 

    ```R
    CREATE EXTERNAL LIBRARY randomForest
    FROM (CONTENT = 'C:\Temp\Rpackages\randomForest_4.6-12.zip')
    WITH (LANGUAGE = 'R');
    ```

    Non è possibile utilizzare un nome arbitrario. il nome della libreria esterna deve avere lo stesso nome che si prevede di utilizzare durante il caricamento o la chiamata del pacchetto.

6. Se la raccolta è stata creata, è possibile eseguire il pacchetto in SQL Server, quando viene chiamata all'interno di una stored procedure.
    
    ```SQL
    EXEC sp_execute_external_script
    @language =N'R',
    @script=N'
    library(randomForest)'
    ```

### <a name="known-issues-with-create-external-library"></a>Problemi noti relativi a creare libreria esterna

Creazione libreria esterna è supportata nei seguenti casi:

+ Si sta installando un singolo pacchetto senza dipendenze.
+ Si siano installando i pacchetti con dipendenze e aver preparato tutti i pacchetti in anticipo. 

L'istruzione DDL ha esito negativo se non sono presenti le dipendenze del pacchetto. Ad esempio, il processo di installazione è noto a non riuscire in questi casi:

+ È stato installato un pacchetto con dipendenze di secondo livello e l'analisi non estende ai pacchetti di secondo livello. Ad esempio, si desidera installare **gglot2**e identificato tutti i pacchetti elencati nel manifesto, ad esempio, tuttavia tali pacchetti era altre dipendenze che non sono stati installati.
+ È stato installato un set di pacchetti che richiedono versioni diverse di un pacchetto di supporto e il server ha la versione non corretta.

## <a name="package-installation-tips"></a>Suggerimenti per l'installazione del pacchetto

In questa sezione fornisce diversi suggerimenti e domande comuni relative all'installazione di pacchetti R in SQL Server.

###  <a name="packageVersion"></a> Ottenere la versione corretta del pacchetto e il formato

Sono presenti più origini per i pacchetti R, ad esempio CRAN e Bioconductor. Il sito ufficiale per il linguaggio R (<https://www.r-project.org/>) elenca molte di queste risorse. Molti pacchetti vengono pubblicati in GitHub, dove è possibile ottenere il codice sorgente. Infine, si potrebbero avere fornito i pacchetti R sviluppati da qualcuno nella propria azienda, o si dispone di un pacchetto personalizzato che è stato scritto.

Indipendentemente dall'origine, prima di tentare di installare il pacchetto, verificare di avere ottenuto il formato binario per la piattaforma Windows. 

### <a name="bkmk_zipPreparation"></a> Scaricare il pacchetto come file compresso

Per l'installazione in un server senza accesso a internet, è necessario scaricare una copia del pacchetto nel formato di un file compresso per l'installazione offline. **Non decomprimere il pacchetto.**

Ad esempio, la procedura seguente descrive adesso per ottenere la versione corretta del [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) pacchetto da Bioconductor, supponendo che il computer abbia accesso a internet.

1.  Nell'elenco **Archivi dei pacchetti** , individuare la versione **binaria di Windows** .

2.  Fare doppio clic sul collegamento per il. File ZIP e selezionare **destinazione Salva come**.

3.  Passare alla cartella locale in cui vengono archiviati, pacchetti compressi e fare clic su **salvare**.

    Questo processo crea una copia locale del pacchetto. 

4. Se si verifica un errore di download, provare a un sito mirror diversi.

5. Dopo aver scaricato l'archivio pacchetti, è possibile installare il pacchetto o copiare il pacchetto compresso in un server che non dispone dell'accesso a internet.

> [!TIP]
> Se per errore, si installa il pacchetto anziché essere scaricato i file binari, una copia del file compresso scaricato viene salvata anche nel computer. Controllare i messaggi di stato mentre il pacchetto viene installato per determinare il percorso del file. È possibile copiare il file compresso per il server che non dispone dell'accesso a internet.
> 
> Tuttavia, quando si ottiene utilizzando questo metodo di pacchetti, le dipendenze non vengono incluse. 

### <a name="bkmk_packageDependencies"></a> Ottenere i pacchetti richiesti

Pacchetti R spesso dipendono da altri più pacchetti, alcuni dei quali potrebbero non essere disponibili nella libreria R predefinito utilizzata dall'istanza. A volte un pacchetto richiede una versione diversa di un pacchetto dipendente che è già installato.

Se è necessario installare più pacchetti o per assicurarsi che tutti gli utenti dell'organizzazione Ottiene il tipo di pacchetto corretto e la versione, è consigliabile utilizzare il [miniCRAN](https://mran.microsoft.com/package/miniCRAN) pacchetto per analizzare la catena di dipendenze completo. minicRAN crea un repository locale che può essere condivisa tra più utenti o computer. Per ulteriori informazioni, vedere [creare un repository di pacchetti locali tramite miniCRAN](create-a-local-package-repository-using-minicran.md).


### <a name="know-which-library-you-are-using-for-installation"></a>Conoscere la libreria che si utilizza per l'installazione

Se in precedenza, è stata modificata l'ambiente R nel computer, prima di installare qualsiasi elemento, sospendere qualche istante e assicurarsi che la variabile di ambiente R `.libPath` Usa un unico percorso.

Questo percorso deve puntare alla cartella R_SERVICES per l'istanza. Per ulteriori informazioni, vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md).

### <a name="side-by-side-installation-with-r-server"></a>Installazione side-by-side con R Server

Se è stato installato Microsoft Machine Learning Server (Standalone) oltre a servizi di SQL Server Machine Learning, il computer deve disporre di installazioni distinte di R per ogni, con i duplicati di tutti gli strumenti di R e librerie.

I pacchetti installati nella raccolta R_SERVER sono utilizzati solo da Microsoft R Server e SQL Server non sono accessibile. Assicurarsi di utilizzare il `R_SERVICES` libreria quando si installano i pacchetti che si desidera utilizzare in SQL Server.

### <a name="how-to-determine-which-packages-are-already-installed"></a>Come determinare quali pacchetti sono già installati?

 Vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md)