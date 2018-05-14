---
title: Installare i nuovi pacchetti di R in servizi di SQL Server Machine Learning | Documenti Microsoft
description: Aggiungere i nuovi pacchetti R per SQL Server 2016 R Services o SQL Server 2017 Machine Learning Services (In-Database)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1106d0f1505f29a3b54f9fc036fcaf28b8715b75
ms.sourcegitcommit: feff98b3094a42f345a0dc8a31598b578c312b38
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2018
---
# <a name="install-new-r-packages-on-sql-server"></a>Installare i nuovi pacchetti di R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come installare i nuovi pacchetti di R a un'istanza di SQL Server in cui è abilitato l'apprendimento. Sono disponibili diversi metodi per l'installazione di nuovi pacchetti di R, a seconda di quale versione di SQL Server in uso e se il server dispone di una connessione a internet.

## <a name="bkmk_rInstall"></a> Installare pacchetti R tramite una connessione Internet

È possibile utilizzare gli strumenti standard di R per installare i nuovi pacchetti in un'istanza di SQL Server 2016 o SQL Server 2017, fornendo il computer dispone di una porta aperta 80 e disporre di diritti di amministratore.

> [!IMPORTANT] 
> Assicurarsi di installare i pacchetti per la libreria predefinita associata con l'istanza corrente. Non installare mai pacchetti in una directory dell'utente.

Questa procedura Usa RGui ma è possibile utilizzare RTerm o qualsiasi altro R della riga di comando dello strumento che supporta l'accesso con privilegi elevato.

### <a name="install-a-package-using-rgui"></a>Installare un pacchetto utilizzando RGui

1. [Determinare il percorso della libreria di istanza](installing-and-managing-r-packages.md). Passare alla cartella in cui sono installati gli strumenti di R. Ad esempio, il percorso predefinito per un'istanza predefinita di SQL Server 2017 è come segue: `C:\Program Files\MSSQL14.MSSQLSERVER\R_SERVICES\bin\x64`

1. RGui.exe e scegliere **Esegui come amministratore**. Se non si dispone delle autorizzazioni necessarie, contattare l'amministratore del database e fornire un elenco dei pacchetti che è necessario.

1. Dalla riga di comando, se si conosce il nome del pacchetto, è possibile digitare: `install.packages("the_package-name")` tra virgolette sono necessarie per il nome del pacchetto.

1. Quando viene richiesto un sito mirror, è possibile selezionare qualsiasi sito a cui è utile per il percorso.

Se il pacchetto di destinazione dipende da pacchetti aggiuntivi, il programma di installazione di R automaticamente le dipendenze vengono scaricate e li installa automaticamente.

Se sono presenti più istanze di SQL Server, ad esempio le istanze side-by-side di SQL Server 2016 R Services e SQL Server 2017 Machine Learning Services, installazione separatamente per ogni istanza se si desidera utilizzare il pacchetto in entrambi i contesti. Pacchetti non possono essere condivisa tra più istanze.

## <a name = "bkmk_offlineInstall"></a> Installazione offline utilizzando gli strumenti di R

Se il server non ha accesso a internet, sono necessari ulteriori passaggi per preparare i pacchetti. Per installare pacchetti R in un server che non dispone dell'accesso a internet, è necessario:

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

2. Aprire la cartella nel server in cui sono installati gli strumenti R per l'istanza. Ad esempio, se si utilizza il prompt dei comandi di Windows in un sistema con SQL Server 2016 R Services, passare al `C:\Program Files\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64`.

3. Fare clic su RGui o RTerm e selezionare **Esegui come amministratore**.

4. Eseguire il comando di R `install.packages` e specificare il pacchetto o nome di repository e il percorso del file ZIP.

    ```R
    install.packages("C:\\Temp\\Downloaded packages\\mynewpackage.zip", repos=NULL)
    ```

    Questo comando consente di estrarre il pacchetto R `mynewpackage` dal file compresso locale, presupponendo che la copia è stato salvato nella directory `C:\Temp\Downloaded packages`, quindi installa il pacchetto nel computer locale. Se il pacchetto contiene tutte le dipendenze, il programma di installazione verifica i pacchetti esistenti nella libreria. Se è stato creato un repository che include le dipendenze, il programma di installazione installa anche i pacchetti richiesti.

    Se tutti i pacchetti necessari non sono presenti nella libreria di istanza e non possono essere disponibile nei file compressi, l'installazione del pacchetto di destinazione non riesce.

## <a name="bkmk_createlibrary"></a> Utilizzo della libreria esterna crea

**Si applica a:**  [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Il [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione consente di aggiungere un pacchetto o un set di pacchetti a un'istanza o un database specifico senza eseguire R o Python code direttamente. Tuttavia, questo metodo richiede la preparazione del pacchetto e le autorizzazioni di database aggiuntivo.

+ Tutti i pacchetti devono essere disponibili come un file compresso locale, anziché scaricati su richiesta da internet.

    Se non si dispone dell'accesso al file system nel server, è inoltre possibile passare un pacchetto completo come una variabile, utilizzando un formato binario. Per ulteriori informazioni, vedere [creare libreria esterna](../../t-sql/statements/create-external-library-transact-sql.md).

+ Tutte le dipendenze devono essere identificate dal nome e la versione e inclusi nel file zip. L'istruzione ha esito negativo se pacchetti richiesti non sono disponibili, tra cui le dipendenze dei pacchetti a valle. Si consiglia di utilizzare **miniCRAN** o **igraph** per l'analisi delle dipendenze di pacchetti. Installazione della versione errata del pacchetto o una dipendenza pacchetto possono causare l'esito negativo dell'istruzione. 

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

## <a name="tips-for-package-installation"></a>Suggerimenti per l'installazione del pacchetto

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


### <a name="know-which-library-you-are-installing-to-and-which-packages-are-already-installed"></a>Conoscere la libreria che si sta installando a e quali pacchetti sono già installati.

Se in precedenza, è stata modificata l'ambiente R nel computer, prima di installare qualsiasi elemento, sospendere qualche istante e assicurarsi che la variabile di ambiente R `.libPath` Usa un unico percorso.

Questo percorso deve puntare alla cartella R_SERVICES per l'istanza. Per altre informazioni, incluse le modalità determinare quali pacchetti sono già installati, vedere [pacchetti R installati con SQL Server](installing-and-managing-r-packages.md).

### <a name="side-by-side-installation-with-standalone-r-or-python-servers"></a>Installazione side-by-side con server Python o Standalone R

Se è installato SQL Server 2017 Microsoft Machine Learning Server (Standalone) o SQL Server 2016 R Server (Standalone) oltre a analitica nel database (SQL Server 2017 Machine Learning Services e SQL Server 2016 R Services), il computer dispone separare le installazioni di R per ognuno, con i duplicati di tutti i strumenti di R e librerie.

I pacchetti installati nella libreria R_SERVER vengono utilizzati solo da un server autonomo e non accessibili da un'istanza di SQL Server (In-Database). Utilizzare sempre il `R_SERVICES` libreria quando si installano pacchetti che si desidera utilizzare nel database in SQL Server.
