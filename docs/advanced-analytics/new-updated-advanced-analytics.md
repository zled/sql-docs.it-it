---
title: 'Aggiornato: avanzato Analitica per i documenti del Server SQL | Documenti Microsoft'
description: Visualizzare i frammenti di contenuto aggiornato per modificati di recente nella documentazione, Analitica avanzato per Microsoft SQL Server.
services: na
documentationcenter: 
author: MightyPen
manager: jhubbard
editor: 
ms.service: 
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 12/02/2017
ms.author: genemi
ms.workload: 
ms.openlocfilehash: c73c6295f7b6e2a23c947ab65160032ce83264e1
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="new-and-recently-updated-advanced-analytics-for-sql-server"></a>Nuovi e aggiornati: Advanced Analitica per SQL Server



Microsoft aggiorna quasi quotidianamente alcuni degli articoli presenti nel sito Web della documentazione [Docs.Microsoft.com](http://docs.microsoft.com/). Questo articolo contiene estratti degli articoli aggiornati di recente. Possono essere indicati anche collegamenti a nuovi articoli.

Questo articolo è generato da un programma che viene rieseguito periodicamente. In alcuni casi un estratto può avere una formattazione imperfetta o essere visualizzato come markdown dell'articolo di origine. Qui le immagini non vengono mai visualizzate.

Sono riportati gli aggiornamenti recenti per l'intervallo di date e l'area di interesse seguenti:



- *Intervallo di date degli aggiornamenti:* &nbsp; **28/09/2017** &nbsp; - &nbsp; **02/12/2017**
- *Area di interesse:* &nbsp; **Analitica avanzate per SQL Server**.

<!-- Repo = 'MicrosoftDocs/sql-docs'.   Branch = 'live'. -->



&nbsp;

## <a name="new-articles-created-recently"></a>Nuovi articoli creati di recente

I collegamenti seguenti consentono di visualizzare nuovi articoli aggiunti di recente.


1. [Aggiungere SQLRUserGroup come utente del database](r/add-sqlrusergroup-to-database.md)
2. [Come utilizzare le funzioni RevoScaleR per trovare o installare pacchetti R in SQL Server](r/use-revoscaler-to-manage-r-packages.md)
3. [Uso di R in Database SQL di Azure](r/using-r-in-azure-sql-database.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Articoli aggiornati con estratti

In questa sezione sono visualizzati gli estratti degli aggiornamenti raccolti dagli articoli che recentemente sono stati sottoposti a un aggiornamento di grande entità.

Gli estratti visualizzati qui sono separati dal relativo contesto semantico. Inoltre è possibile che un estratto sia talvolta separato da importanti elementi di sintassi markdown che lo circondano nell'articolo vero e proprio. Di conseguenza, questi estratti devono essere usati solo come indicazioni generali. Gli estratti consentono solo di comprendere se sia utile o meno consultare l'articolo completo.

Per queste e altre ragioni, non copiare codice da questi estratti e non prendere come verità assoluta ciò che si legge negli estratti. Consultare gli articoli completi.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Elenco compatto degli articoli aggiornati di recente

Questo elenco compatto include i collegamenti a tutti gli articoli aggiornati elencati nella sezione degli estratti.

1. [Problemi noti in servizi di Machine Learning](#TitleNum_1)
2. [Creare un repository di pacchetti locale usando miniCRAN](#TitleNum_2)
3. [Determinare quali pacchetti R vengono installati in SQL Server](#TitleNum_3)
4. [Installare pacchetti R aggiuntivi su SQL Server](#TitleNum_4)
5. [L'installazione delle funzionalità in una macchina virtuale Azure di apprendimento automatico di SQL Server](#TitleNum_5)
6. [Installare training preliminare di machine learning i modelli in SQL Server](#TitleNum_6)
7. [Evitare gli errori di pacchetti R installati nelle librerie utente](#TitleNum_7)
8. [Eseguire il provisioning di una macchina virtuale per machine learning in Azure](#TitleNum_8)
9. [RevoScaleR](#TitleNum_9)
10. [Abilitare o disabilitare la gestione dei pacchetti R per SQL Server](#TitleNum_10)
11. [Configurare un client di analisi scientifica dei dati per l'utilizzo con SQL Server](#TitleNum_11)
12. [Configurare SQL Server Machine Learning Services (In-Database)](#TitleNum_12)
13. [Installazione automatica di Machine Learning Services (In-Database)](#TitleNum_13)
14. [Passaggio 3: Esplorare e visualizzare i dati](#TitleNum_14)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-known-issues-in-machine-learning-servicesknown-issues-for-sql-server-machine-learning-servicesmd"></a>1. &nbsp;[Problemi noti di servizi di Machine Learning](known-issues-for-sql-server-machine-learning-services.md)

*Ultimo aggiornamento: 2017-11-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Avanti](#TitleNum_2))

<!-- Source markdown line 321.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 00121c648c21576d5c86494137de1d4d81e2e265 c65973f6ae9253af5ecc621916ef36d7c0398789  (PR=3980  ,  Filename=known-issues-for-sql-server-machine-learning-services.md  ,  Dirpath=docs\advanced-analytics\  ,  MergeCommitSha40=06bb91d138a4d6395c7603a2d8f99c69a20642d3) -->



**Esecuzione del codice Python o problemi di pacchetti Python**


In questa sezione contiene i problemi noti specifici all'esecuzione di Python su SQL Server, nonché i problemi relativi ai pacchetti Python pubblicati da Microsoft, tra cui [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) e [microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).

**Chiamata al modello con training preliminare non riesce se il percorso al modello è troppo lungo**


Se si installano i modelli con training preliminare in un'installazione predefinita, a seconda del nome del computer e il nome dell'istanza, il percorso completo risulta nel file di modello con training potrebbe essere troppo lungo per Python da leggere. Questa limitazione verrà risolto in una prossima service release.

Esistono diverse potenziali soluzioni alternative:

+ Quando si installa i modelli con training preliminare, scegliere un percorso personalizzato.
+ Se possibile, installare l'istanza di SQL Server in un percorso di installazione personalizzato, ad esempio C:\SQL\MSSQL14. MSSQLSERVER.
+ Utilizzare l'utilità Windows [Fsutil](https://technet.microsoft.com/library/cc788097(v=ws.11).aspx) per creare un collegamento fisso che esegue il mapping a un percorso più breve il file del modello.

**Errore di inizializzazione di una variabile di tipo varbinary causa un errore in BxlServer**


Se si esegue codice Python in SQL Server utilizzando `sp_execute_external_script`e il codice include variabili di tipo varbinary (max), varchar (max) o tipi simili di output, la variabile deve essere inizializzata o impostare come parte dello script. In caso contrario, il componente di scambio di dati, BxlServer, genera un errore e smette di funzionare.

Questa limitazione verrà risolto in una prossima service release. In alternativa, assicurarsi che la variabile viene inizializzata all'interno dello script Python. Qualsiasi valore valido può essere utilizzato, come negli esempi seguenti:

```sql
declare @b varbinary(max);
exec sp_execute_external_script
  @language = N'Python'
```



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-create-a-local-package-repository-using-minicranrcreate-a-local-package-repository-using-minicranmd"></a>2. &nbsp;[Creare un repository di pacchetti locali tramite miniCRAN](r/create-a-local-package-repository-using-minicran.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_1) | [Avanti](#TitleNum_3))

<!-- Source markdown line 43.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 44b77cb127e9ffab1777216a66f0e5be9c82f3d2 65e30f10fc36acb3ce95f60f51f3501fbc98ad08  (PR=4150  ,  Filename=create-a-local-package-repository-using-minicran.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



-   **Più facile installazione offline**: installare il pacchetto a un server non in linea richiede che è anche di scaricare tutte le dipendenze di pacchetto, tramite miniCRAN rende più semplice ottenere tutte le dipendenze nel formato corretto.

-   **Gestione della versione migliorata**: In un ambiente multiutente, esistono buone ragioni per evitare l'installazione senza restrizioni di più versioni del pacchetto nel server.

Dopo aver creato il repository, è possibile modificarla in aggiungendo nuovi pacchetti o l'aggiornamento della versione dei pacchetti esistenti.

**Passaggio 1. Installare il pacchetto miniCRAN**


Iniziare creando un repository miniCRAN da utilizzare come origine. In un computer con accesso a internet, è necessario creare questo repository.

1.  Installare il pacchetto miniCRAN e obbligatorio **igraph** pacchetto.

```
    if(!require("miniCRAN")) install.packages("miniCRAN") if(!require("igraph"))
    install.packages("igraph") library(miniCRAN)
```

**Passaggio 2. Definire un'origine del pacchetto: un mirror CRAN o uno snapshot MRAN**


1. Specificare un sito mirror da utilizzare nel recupero dei pacchetti.

```
    CRAN_mirror \<- c(CRAN = "https://mran.microsoft.com/snapshot/2017-08-01")
```

2.  Indicare una cartella locale in cui archiviare i pacchetti raccolti. È necessario che denominare la cartella miniCRAN; potrebbe essere un nome più descrittivo, ad esempio "GeneticsPackages" o "ClientRPackages1.0.2".

    Assicurarsi solo creare la cartella in anticipo. Viene generato un errore se il `local_repo` cartella non esiste quando si esegue il codice R in un secondo momento.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-determine-which-r-packages-are-installed-on-sql-serverrdetermine-which-packages-are-installed-on-sql-servermd"></a>3. &nbsp;[Determinare quali pacchetti R vengono installati in SQL Server](r/determine-which-packages-are-installed-on-sql-server.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_2) | [Avanti](#TitleNum_4))

<!-- Source markdown line 55.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 13d93acedc6e6b4615f1a244a2a1542910feb69e 9a065066398843a4bed318fa46d4982d712915a9  (PR=4150  ,  Filename=determine-which-packages-are-installed-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



+ Se il pacchetto viene trovato, il messaggio restituito deve essere un'operazione quale "Comandi vengano eseguiti correttamente."

+ Se è Impossibile trovare o caricare il pacchetto, si verifica un errore simile al seguente: "si è verificato un errore dello script esterno: errore in library("RevoScaleR"): nessun pacchetto RevoScaleR chiamato"

**Ottenere un elenco dei pacchetti installati con R**


Esistono diversi modi per ottenere un elenco dei pacchetti installati o caricati con gli strumenti R e le funzioni R. Molti strumenti di sviluppo di R forniscono un visualizzatore oggetti o un elenco dei pacchetti che vengono installati o caricati nell'area di lavoro corrente di R.

+ Da un'utilità R locale, utilizzare una funzione R di base, ad esempio `installed.packages()`, incluso nel `utils` pacchetto. Per ottenere un elenco che è preciso per un'istanza, è necessario specificare in modo esplicito il percorso di libreria o utilizzare gli strumenti di R associati con la libreria di istanza.

+ Per verificare se un pacchetto in un contesto di calcolo specifico, è possibile utilizzare le funzioni seguenti dal pacchetto RevoScaleR. Queste funzioni consentono di identificare i pacchetti in contesti di calcolo specificata:

+ [rxFindPackage](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxfindpackage)

+ [rxInstalledPackages](https://msdn.microsoft.com/microsoft-r/scaler/packagehelp/rxinstalledpackages)

Ad esempio, eseguire il seguente codice R per ottenere un elenco dei pacchetti disponibili nel contesto di calcolo specificato di SQL Server.

```r
sqlServerCompute <- RxInSqlServer(connectionString = "Driver=SQL Server;Server=myServer;Database=TestDB;Uid=myID;Pwd=myPwd;")
sqlPackages <- rxInstalledPackages(computeContext = sqlServerCompute)
sqlPackages
```
**Vedere anche**




&nbsp;

&nbsp;

---

<a name="TitleNum_4"/>

### <a name="4-nbsp-install-additional-r-packages-on-sql-serverrinstall-additional-r-packages-on-sql-servermd"></a>4. &nbsp;[Installare pacchetti R aggiuntivi su SQL Server](r/install-additional-r-packages-on-sql-server.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_3) | [Avanti](#TitleNum_5))

<!-- Source markdown line 266.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ba48f1838857d90d6692aafc48f393777ac602fa 37de2586a344a99969bcd9a20723c021db2604a4  (PR=4150  ,  Filename=install-additional-r-packages-on-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



In questa sezione fornisce diversi suggerimenti e codice di esempio relativi all'installazione del pacchetto R in SQL Server.

**<a name="packageVersion"></a>Ottenere la versione corretta del pacchetto e il formato**


Sono presenti più origini per i pacchetti R, le più note sono CRAN e Bioconductor. Il sito ufficiale per il linguaggio R (<https://www.r-project.org/>) elenca molte di queste risorse. Molti pacchetti vengono pubblicati in GitHub, dove è possibile ottenere il codice sorgente. Tuttavia, si potrebbero avere ottenuto il pacchetti R sviluppati da qualcuno nella propria azienda.

Indipendentemente dall'origine, è necessario assicurarsi che il pacchetto da installare è in formato binario per la piattaforma Windows. In caso contrario, il pacchetto scaricato non è possibile eseguire nell'ambiente di SQL Server.

Prima di scaricare, controllare anche se il pacchetto è compatibile con la versione di R in esecuzione in SQL Server.

**<a name="bkmk_zipPreparation"></a>Download del pacchetto come file compresso**


Per l'installazione in un server senza accesso a internet, scaricare una copia del pacchetto nel formato di un file compresso per l'installazione offline. Non decomprimere il pacchetto.

Ad esempio, la procedura seguente descrive adesso per ottenere la versione corretta del [FISHalyseR](http://bioconductor.org/packages/release/bioc/html/FISHalyseR.html) pacchetto da Bioconductor, supponendo che il computer abbia accesso a internet.

1.  Nell'elenco **Archivi dei pacchetti** , individuare la versione **binaria di Windows** .

2.  Fare doppio clic sul collegamento per il. File ZIP e selezionare **destinazione Salva come**.

3.  Passare alla cartella locale in cui vengono archiviati, pacchetti compressi e fare clic su **salvare**.

Questo processo crea una copia locale del pacchetto. È quindi possibile installare il pacchetto o copiare il pacchetto compresso in un server che non dispone dell'accesso a internet.

Per ulteriori informazioni sui contenuti del formato di file zip e come creare un pacchetto R, si consiglia di questa esercitazione, che è possibile scaricare in formato PDF dal sito del progetto R: [la creazione di pacchetti R](http://cran.r-project.org/doc/contrib/Leisch-CreatingPackages.pdf).



&nbsp;

&nbsp;

---

<a name="TitleNum_5"/>

### <a name="5-nbsp-installing-sql-server-machine-learning-features-on-an-azure-virtual-machinerinstalling-sql-server-r-services-on-an-azure-virtual-machinemd"></a>5. &nbsp;[Computer l'installazione di SQL Server apprendimento delle funzionalità in una macchina virtuale di Azure](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_4) | [Avanti](#TitleNum_6))

<!-- Source markdown line 55.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f4d287044b8bfda2dbe77fbf65b0d9cdd8f2ff42 2a8e33de6383f5d3af52256c5dfcb60184659eb8  (PR=4150  ,  Filename=installing-sql-server-r-services-on-an-azure-virtual-machine.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



6. Se si prevede di connettersi all'istanza da un client di analisi scientifica dei dati remoti, completare [ulteriori passaggi, # passaggi additional) in base alle esigenze.

**Disabilitare le funzionalità di machine learning in una macchina virtuale di SQL Server**


È inoltre possibile abilitare o disabilitare la funzionalità in una macchina virtuale di SQL Server esistente in qualsiasi momento.

1. Aprire il pannello della macchina virtuale.
2. Fare clic su **Impostazioni** e selezionare **Configurazione di SQL Server**.
3. Apportare modifiche alle funzionalità e si applicano.

**<a name="existing"></a>Aggiungere R Services a una macchina virtuale esistente SQL Server 2016 Enterprise**


Se si crea una macchina virtuale di Azure che incluso SQL Server senza di machine learning, è possibile aggiungere la funzionalità attenendosi alla procedura seguente:

1. Eseguire di nuovo.... Includi-NotShown - ssNoVersion--... /.. /Includes/ssnoversion-MD.MD]) del programma di installazione e aggiungere la funzionalità di **configurazione Server** pagina della procedura guidata.
2. Abilitare l'esecuzione di script esterni e riavviare il.... Includi-NotShown - ssNoVersion--... /.. istanza /Includes/ssnoversion-MD.MD]). Per ulteriori informazioni, vedere [impostato backup di SQL Server R Services,... /.. / advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facoltativo) Configurare l'accesso al database per gli account di lavoro R, se necessario per l'esecuzione di script remoti.
   Per ulteriori informazioni, vedere [impostare backup di SQL Server R Services,... /.. / advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facoltativo) Modificare una regola del firewall nella macchina virtuale di Azure, se si intende consentire l'esecuzione di script R dai client di data science remoti. Per ulteriori informazioni, vedere [Unblock firewall-#firewall).
4. Installare o abilitare le librerie di rete necessarie. Per ulteriori informazioni, vedere [Aggiungi rete protocolli-#network).



&nbsp;

&nbsp;

---

<a name="TitleNum_6"/>

### <a name="6-nbsp-install-pretrained-machine-learning-models-on-sql-serverrinstall-pretrained-models-sql-servermd"></a>6. &nbsp;[Installazione pretrained modelli di machine learning in SQL Server](r/install-pretrained-models-sql-server.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_5) | [Avanti](#TitleNum_7))

<!-- Source markdown line 96.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 07b51584a90568cccceea382c44155e40e09c967 db083f8536fbb2ea5886fed787872867b5de5750  (PR=4150  ,  Filename=install-pretrained-models-sql-server.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    For example, to enable use of the latest version of the pretrained models for Python, in a default instance of SQL Server 2017, you would run this statement:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    On a named instance, the command would be something like this:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\MSSQL14.MyInstanceName\PYTHON_SERVICES\library\MicrosoftML\mxLibs\x64"`

    + Per utilizzare Python pretrained modelli con Machine Learning Server (Standalone):

    `RSetup.exe /install /component MLM /version <version> /language 1033 /destdir "<sql_folder>\PYTHON_SERVER\site-packages\microsoftml\mxLibs"`

    Ad esempio, presupponendo un'installazione predefinita di Machine Learning Server (Standalone) utilizzando il programma di installazione di SQL Server 2017, eseguire l'istruzione seguente:

    `RSetup.exe /install /component MLM /version 9.2.0.24 /language 1033 /destdir "C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER\Lib\site-packages\microsoftml\mxLibs"`

5. I valori seguenti sono supportati per il parametro version:



&nbsp;

&nbsp;

---

<a name="TitleNum_7"/>

### <a name="7-nbsp-avoiding-errors-on-r-packages-installed-in-user-librariesrpackages-installed-in-user-librariesmd"></a>7. &nbsp;[Evitare gli errori di pacchetti R installati nelle librerie utente](r/packages-installed-in-user-libraries.md)

*Ultimo aggiornamento: 2017-10-23* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_6) | [Avanti](#TitleNum_8))

<!-- Source markdown line 33.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 52cb9a53d7d9c31ee9bc6977464ebd2a18081ff3 3537aa6755c66f12c19bb3448dc9b5c8abb9cc28  (PR=3619  ,  Filename=packages-installed-in-user-libraries.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=aecf422ca2289b2a417147eb402921bb8530d969) -->



Tuttavia, ciò non possa mai funzionare durante l'esecuzione di soluzioni R in SQL Server, perché i pacchetti R devono essere installati in una raccolta predefinito specifico che viene associata all'istanza.

Se il pacchetto non è installato nella libreria predefinita, potrebbe essere visualizzato un errore analogo al seguente quando si tenta di chiamare il pacchetto:

*Errore in library(xxx): nessun pacchetto denominato 'package-name'*

È inoltre una procedura di sviluppo non valido per installare i pacchetti R richiesti in una raccolta di utente personalizzato, come può causare errori se una soluzione viene eseguita da un altro utente che non ha accesso al percorso di libreria.

**Come installare i pacchetti R in una libreria accessibile**


**Per SQL Server 2016**

Utilizzare la libreria di pacchetto associata all'istanza. Per informazioni dettagliate, vedere [pacchetti R installati con SQL Server--installing-and-managing-r-packages.md)

**Per SQL Server 2017**

SQL Server fornisce funzionalità che consentono di gestire più versioni del pacchetto e concedere agli utenti le autorizzazioni per singoli pacchetti, senza richiedere che gli utenti hanno accesso al file system.

Per informazioni dettagliate su come impostare una libreria condivisa pacchetto e assegnare utenti a ruoli, vedere [gestione dei pacchetti R per SQL Server--r-package-management-for-sql-server-r-services.md.)




&nbsp;

&nbsp;

---

<a name="TitleNum_8"/>

### <a name="8-nbsp-provision-a-virtual-machine-for-machine-learning-on-azurerprovision-the-r-server-only-sql-server-2016-enterprise-vm-on-azuremd"></a>8. &nbsp;[Effettuare il provisioning di una macchina virtuale per machine learning in Azure](r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)

*Ultimo aggiornamento: 2017-10-31* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_7) | [Avanti](#TitleNum_9))

<!-- Source markdown line 132.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 16439b4a8f5f4218edfcd746ed20ccbc8263dabc 1b3a8a7d1ceceaa459b3fd5640da26859df8d80b  (PR=3748  ,  Filename=provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=262e3cf5df2448bb6b532c0549c3d72daefe5a96) -->



|nome| Commenti|
|----|----|----|
| **SQL Server 2016**| ***  |
|SQL Server 2016 Enterprise Edition SP1 in Windows|R Services per integrata analitica avanzate.|
|BYOL SQL Server 2016 SP1 Enterprise in Windows Server |R Services per integrata analitica avanzate. |
|Licenza gratuita: SQL Server 2016 Developer SP1 in Windows Server 2016 |R Services per integrata analitica avanzate. |
| Macchina virtuale di analisi scientifica dei dati - Windows 2012|Contiene i comuni strumenti di analisi scientifica dei dati, incluso Microsoft R Server Developer Edition, SQL Server 2016 Developer edition, distribuzione Anaconda Python, Julia Pro developer edition e notebook Jupyter per R.|
| Macchina virtuale di analisi scientifica dei dati - 2016 Windows|Include SQL Server 2016 Developer Edition, con supporto per analitica R nel database.|
|**SQL Server 2017**| ***   |
|SQL Server 2017 Enterprise Windows Server 2016| Servizi di Machine Learning con supporto del linguaggio Python e R.|
|BYOL SQL Server 2017 Enterprise Windows Server 2016|Servizi di Machine Learning con supporto del linguaggio Python e R.|
| Licenza di gratuita di SQL Server: SQL Server 2017 Developer Edition in Windows Server|Servizi di Machine Learning con supporto del linguaggio Python e R.|
| **Altro**| *** |
| Machine Learning Server solo SQL Server 2017 Enterprise|Simile all'immagine di SQL Server 2016 Enterprise Edition, ma contiene la versione autonoma di Server di Machine Learning e ha core ScaleR e funzionalità di rendere operativo ottimizzato per Windows ambienti.|
| Server di Machine Learning per Windows|Contiene la versione autonoma di Machine Learning Server, con funzionalità di rendere operativo ottimizzata per ambienti Windows.|



&nbsp;

&nbsp;

---

<a name="TitleNum_9"/>

### <a name="9-nbsp-revoscalerrrevoscaler-overviewmd"></a>9. &nbsp;[RevoScaleR](r/revoscaler-overview.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_8) | [Avanti](#TitleNum_10))

<!-- Source markdown line 18.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 92f2dfa2e75037a932415881c55d2fd37fc6847a c6e9f17f2df82447b18beff41769ae3ebfbed562  (PR=4150  ,  Filename=revoscaler-overview.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->




RevoScaleR è un pacchetto delle funzioni di machine learning, fornito da Microsoft, che supporta l'analisi scientifica dei dati su larga scala.

+ Funzioni supportano l'importazione dei dati, la trasformazione dei dati, riepilogo, visualizzazione e analisi.

+ _Su larga scala_ significa che operazioni possono essere eseguite sul set di dati molto grandi, in parallelo e distribuite nel file System. Gli algoritmi possono operare su set di dati che non rientrano nella memoria, utilizzando la suddivisione in blocchi e il riassemblaggio risultati una volta completate le operazioni.

+ RevoScaleR offre numerosi miglioramenti rispetto funzioni R open source. Sono disponibili funzioni RevoScaleR corrispondente a molte delle funzioni R più diffuse base. Le funzioni RevoScaleR vengono indicate con un **rx** o **Rx** prefisso per facilitarne l'identificazione.

+ RevoScaleR funge da una piattaforma per l'analisi scientifica dei dati distribuiti. Ad esempio, è possibile utilizzare le trasformazioni e contesti di calcolo RevoScaleR con gli algoritmi avanzati di [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). È inoltre possibile utilizzare [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) per eseguire funzioni di base R in parallelo.

Per esempi di RevoScaleR in azione, vedere i blog:

+ [Compilare e distribuire un modello predittivo con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Un milione di stime con Machine Learning Server al secondo](https://blogs.msdn.microsoft.com/mlserver/2017/10/15/1-million-predictionssec-with-machine-learning-server-web-service/)

+ [Stima dei suggerimenti taxi utilizzando MicrosoftML](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/01/17/predicting-nyc-taxi-tips-using-microsoftml/)

+ [Ottimizzazione delle prestazioni con rxExec](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/11/14/performance-optimization-when-using-rxexec-to-parallelize-algorithms/)

**Come ottenere RevoScaleR**




&nbsp;

&nbsp;

---

<a name="TitleNum_10"/>

### <a name="10-nbsp-enable-or-disable-r-package-management-for-sql-serverrr-package-how-to-enable-or-disablemd"></a>10. &nbsp;[Abilitare o disabilitare la gestione dei pacchetti R per SQL Server](r/r-package-how-to-enable-or-disable.md)

*Ultimo aggiornamento: 2017-11-30* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_9) | [Avanti](#TitleNum_11))

<!-- Source markdown line 60.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 5f846cd7d601459a95e694ada41e9fc5285f3de9 83a4a84adf47670c7fd4599f889f27ec3c219708  (PR=4150  ,  Filename=r-package-how-to-enable-or-disable.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    If you do not specify a user, the current security context is used.

3. Ripetere il comando per ogni database in cui installare i pacchetti.

4.  Per verificare che i nuovi ruoli sono stati creati correttamente, in SQL Server Management Studio, fare clic sul database, espandere **sicurezza**, espandere **ruoli predefiniti del Database**.

    È anche possibile eseguire una query su Sys. database_principals, ad esempio le operazioni seguenti:

```sql
    SELECT pr.principal_id, pr.name, pr.type_desc,
        pr.authentication_type_desc, pe.state_desc,
        pe.permission_name, s.name + '.' + o.name AS ObjectName
    FROM sys.database_principals AS pr
    JOIN sys.database_permissions AS pe
        ON pe.grantee_principal_id = pr.principal_id
    JOIN sys.objects AS o
        ON pe.major_id = o.object_id
    JOIN sys.schemas AS s
        ON o.schema_id = s.schema_id;
```

4.  Dopo aver abilitata la funzionalità, è possibile usare qualsiasi utente che disponga delle autorizzazioni appropriate di [creare libreria esterna](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql) istruzione T-SQL per aggiungere i pacchetti. Per un esempio del funzionamento, vedere [installare pacchetti aggiuntivi su SQL Server](r/install-additional-r-packages-on-sql-server.md).

**<a name="bkmk_disable"></a>Disabilitare la gestione dei pacchetti**




&nbsp;

&nbsp;

---

<a name="TitleNum_11"/>

### <a name="11-nbsp-set-up-a-data-science-client-for-use-with-sql-serverrset-up-a-data-science-clientmd"></a>11. &nbsp;[Impostare un client di analisi scientifica dei dati per l'utilizzo con SQL Server](r/set-up-a-data-science-client.md)

*Ultimo aggiornamento: 2017-11-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_10) | [Avanti](#TitleNum_12))

<!-- Source markdown line 52.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f674f5d329211e4c7d8dc464bd70f1cdef633350 8c65fc96c04f32d1e4777870774a11f9fd2ee219  (PR=3765  ,  Filename=set-up-a-data-science-client.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=dc67a9c744441f9d556e98fb9a4daf4414060360) -->



    For setup information, see [How to install R Tools for Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).

    To configure RTVS to use your Microsoft R client libraries, see [About Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

+ Visual Studio 2017

    Anche l'edizione gratuita Community include dati scienza carico di lavoro, che installa i modelli di progetto per R, Python e F #.

    Scaricare Visual Studio da [questo sito](https://www.visualstudio.com/vs/).

+ RStudio

    Se si preferisce usare RStudio, sono necessari alcuni passaggi aggiuntivi per usare le librerie RevoScaleR:

    - Installare il Client di Microsoft R per ottenere i pacchetti necessari e le librerie.
    - Aggiornare il percorso di R per utilizzare il runtime di Microsoft R.

    Per ulteriori informazioni, vedere [Client R - configurare l'IDE](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client#step-2-configure-your-ide).

**Configurare l'IDE**


+ R Tools for Visual Studio

    Vedere [questo sito](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r) per alcuni esempi di come compilare ed eseguire il debug R progetti utilizzando strumenti R per Visual Studio.

+ Visual Studio 2017

    Se si installa Microsoft R Client o Server R **prima** si installa Visual Studio, le librerie di R Server vengono automaticamente rilevate e utilizzate per il percorso della libreria. Se non è installato, le librerie di RevoScaleR dal **strumenti R** dal menu **installa R Client**.

**Eseguire R in SQL Server**


Questo esempio viene utilizzato Visual Studio 2017 Community Edition, con il carico di lavoro dell'analisi scientifica dei dati installato.

1. Dal **File** dal menu **New** e quindi selezionare **progetto**.

2. -L'icona della mano riquadro contiene un elenco di modelli preinstallati. Fare clic su **R**e selezionare **R progetto**. Nel **nome** digitare `dbtest` e fare clic su **OK**.



&nbsp;

&nbsp;

---

<a name="TitleNum_12"/>

### <a name="12-nbsp-set-up-sql-server-machine-learning-services-in-databaserset-up-sql-server-r-services-in-databasemd"></a>12. &nbsp;[Configurare SQL Server Machine Learning Services (In-Database)](r/set-up-sql-server-r-services-in-database.md)

*Ultimo aggiornamento: 2017-11-16* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_11) | [Avanti](#TitleNum_13))

<!-- Source markdown line 111.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 4d355f6494b417dd90dce3943e7176eaece7336e 20bddb8ffd4cf3774b812a7376c70b95ccc57e92  (PR=3980  ,  Filename=set-up-sql-server-r-services-in-database.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=06bb91d138a4d6395c7603a2d8f99c69a20642d3) -->



   + Servizi motore di database
   + R Services (In-Database)

7. Quando l'installazione è stata completata, riavviare il computer.


**<a name="bkmk2017top"></a>Installare SQL Server 2017 Machine Learning Services (In-Database)**


> [!div class="checklist"]
> * Installare il motore di database e le funzionalità di apprendimento automatico
> * Necessari passaggi di post-installazione: abilitare l'apprendimento e riavviare
> * Passaggi di post-installazione facoltativi: aggiungere regole del firewall, gli utenti di aggiungere, modificare o configurare gli account di servizio, configurare un client di analisi scientifica dei dati remota.

**Introduzione**

1. Correre..! Includi-NotShown - ssNoVersion--... /.. programma di installazione /Includes/ssnoversion-MD.MD]).

2. Nel **installazione** , selezionare **nuova installazione SQL Server autonomo o aggiungere funzionalità a un'installazione esistente**.

     ! [Installare servizi di Machine Learning (In-Database)--media/2017setup-installation-page-mlsvcs.png "Avviare l'installazione del motore di database con servizi di Machine Learning")

3. Nel **Selezione funzionalità** pagina, selezionare le opzioni seguenti:

    + Selezionare **servizi motore di Database**. Il motore di database, è necessario in ogni istanza che usa il machine learning.

    + Selezionare **di Machine Learning Services (In-Database)**. Questa opzione installa il supporto per l'utilizzo nel database di R. Dopo aver selezionato questa opzione, è possibile selezionare di machine learning language. È possibile selezionare solo R oppure è possibile aggiungere sia R e Python.

    ! [Funzionalità Servizi Learning macchina selection--media/2017setup-features-page-mls-rpy.png "selezionare queste funzionalità per R Services nel Database")

    Se non si seleziona Opzioni di linguaggio Python o R, l'installazione guidata installa solo il framework di estendibilità, che include Launchpad attendibile di SQL Server e non installa i componenti specifici della lingua.  In genere si consiglia di installare almeno una lingua con cui iniziare. Tuttavia, è possibile utilizzare questa opzione se si prevede di utilizzare immediatamente il processo di associazione per l'aggiornamento di machine learning componenti. Per ulteriori informazioni, vedere [utilizzare SqlBindR per aggiornare un'istanza di R Services--use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).



&nbsp;

&nbsp;

---

<a name="TitleNum_13"/>

### <a name="13-nbsp-unattended-installation-of-machine-learning-services-in-databaserunattended-installs-of-sql-server-r-servicesmd"></a>13. &nbsp;[Installazione automatica di Machine Learning Services (In-Database)](r/unattended-installs-of-sql-server-r-services.md)

*Ultimo aggiornamento: 2017-11-01* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([precedente](#TitleNum_12) | [Avanti](#TitleNum_14))

<!-- Source markdown line 75.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ad203c90adff3f515b5f16472fad9753be7a421d 6925a9276bcd4a80babc7504de50400f1a5a2940  (PR=3765  ,  Filename=unattended-installs-of-sql-server-r-services.md  ,  Dirpath=docs\advanced-analytics\r\  ,  MergeCommitSha40=dc67a9c744441f9d556e98fb9a4daf4414060360) -->



L'esempio seguente mostra gli argomenti necessari per eseguire un invisibile all'utente, automatica installazione di SQL Server 2017 macchina Services (In-Database) con il linguaggio Python aggiunto.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

Si noti il flag necessari per Python in SQL Server 2017:

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MPY`
+ `IACCEPTPYTHONOPENLICENSETERMS`

**Installare R sia Python in un'istanza denominata**


Nell'esempio seguente visualizza gli argomenti necessari per eseguire un invisibile all'utente, automatica di installazione di SQL Server 2017 macchina Services (In-Database) in un'istanza denominata. Vengono aggiunti i linguaggi sia R e Python.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER.ServerName /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

**<a name="OldInstall"></a>Installazione della riga di comando per SQL Server 2016**


L'esempio seguente mostra gli argomenti necessari per eseguire un invisibile all'utente, automatica di installazione di SQL Server 2016 con il linguaggio R aggiunto.



&nbsp;

&nbsp;

---

<a name="TitleNum_14"/>

### <a name="14-nbsp-step-3-explore-and-visualize-the-datatutorialssqldev-py3-explore-and-visualize-the-datamd"></a>14. &nbsp;[Passaggio 3: esplorare e visualizzare i dati](tutorials/sqldev-py3-explore-and-visualize-the-data.md)

*Aggiornamento: 30/11/2017* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Precedente](#TitleNum_13))

<!-- Source markdown line 66.  ms.author= "jeannt".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 47edcfbd8da7cf1ea1ad03a05f86d3cd26014827 674a7c7d0e8290fc91970ed2aeda3b97d5165d75  (PR=4150  ,  Filename=sqldev-py3-explore-and-visualize-the-data.md  ,  Dirpath=docs\advanced-analytics\tutorials\  ,  MergeCommitSha40=578bd1c2760866ddeb3523f830cfc3cb6b4ab9af) -->



    Class 4: `tip_amount` > $20

**Creare grafici usando Python in T-SQL**


Lo sviluppo di una soluzione di analisi scientifica dei dati prevede in genere frequenti esplorazioni e visualizzazioni dei dati. Poiché la visualizzazione è un potente strumento per le informazioni sulla distribuzione dei dati e gli outlier, Python fornisce molti pacchetti per la visualizzazione dati. Il **matplotlib** modulo è una delle librerie più comuni per la visualizzazione e include numerose funzioni per la creazione di istogrammi, grafici a dispersione, casella grafici e altri grafici di esplorazione dei dati.

In questa sezione, è illustrato come utilizzare i grafici tramite le stored procedure. Invece di aprire l'immagine nel server, archiviare l'oggetto di Python `plot` come **varbinary** dati e quindi scrivere che in un file che possono essere condivisi o visualizzati in un' posizione.

**Creare un tracciato come dati varbinary**


Il **revoscalepy** modulo incluso in servizi di SQL Server 2017 Machine Learning supporta funzionalità simili a quelli di **RevoScaleR** pacchetto per R.  Questo esempio viene utilizzato l'equivalente di Python di `rxHistogram` per tracciare un istogramma in base ai dati da un.... Includi-NotShown - tsql:... /.. query /Includes/TSQL-MD.MD]).

La stored procedure restituisce un Python serializzato `figure` oggetto come flusso di **varbinary** dati. Non è possibile visualizzare direttamente i dati binari, ma è possibile usare il codice Python da deserializzare e visualizzare le cifre nel client e quindi salvare il file di immagine in un computer client.

1. Creare la stored procedure _SerializePlots_, se lo script di PowerShell non è già eseguita questa operazione.

    - La variabile `@query` definisce il testo della query `SELECT tipped FROM nyctaxi_sample`, che viene passato al blocco di codice Python come argomento per la variabile di input di script, `@input_data_1`.
    - Lo script Python è piuttosto semplice: **matplotlib** `figure` gli oggetti vengono utilizzati per eseguire il tracciato istogramma e a dispersione e questi oggetti vengono quindi serializzati utilizzando il `pickle` libreria.







## <a name="similar-articles"></a>Articoli simili

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

In questa sezione sono elencati articoli molto simili ad articoli aggiornati di recente in altre aree di interesse all'interno del repository GitHub pubblico di Microsoft: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### <a name="subject-areas-which-do-have-new-or-recently-updated-articles"></a>Aree di interesse con articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (3+14): documentazione di **Advanced Analytics per SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Nuovo + aggiornato (1+0): **Analysis Services for SQL (Analysis Services per SQL)** Docs](../analysis-services/new-updated-analysis-services.md)
- [Nuovo + aggiornato (87+0): documentazione della **piattaforma di strumenti analitici per SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [Nuovo + aggiornato (5+4): documentazione della **connessione a SQL Server**](../connect/new-updated-connect.md)
- [Nuovo + aggiornato (0+1): documentazione del **motore di database di SQL Server**](../database-engine/new-updated-database-engine.md)
- [Nuovo + aggiornato (2+2): documentazione di **SQL Server Integration Services**](../integration-services/new-updated-integration-services.md)
- [Nuovo + aggiornato (10+9): documentazione di **Linux per SQL Server**](../linux/new-updated-linux.md)
- [Nuovo + aggiornato (2+4): documentazione dei **database relazionali per SQL Server**](../relational-databases/new-updated-relational-databases.md)
- [Nuovo + aggiornato (4+2): documentazione di **SQL Server Reporting Services**](../reporting-services/new-updated-reporting-services.md)
- [Nuovo + aggiornato (0+1): documentazione degli **esempi per SQL Server**](../sample/new-updated-sample.md)
- [Nuovo + aggiornato (21+0): documentazione di **SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Nuovo + aggiornato (5+1): documentazione di **Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Nuovo + aggiornato (0+1): **SQL Server Data Tools (SSDT)** Docs](../ssdt/new-updated-ssdt.md)
- [Nuovo + aggiornato (1+0): documentazione di **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Nuovo + aggiornato (0+1): **SQL Server Management Studio (SSMS)** Docs](../ssms/new-updated-ssms.md)
- [Nuovo + aggiornato (0+2): documentazione di **Transact-SQL**](../t-sql/new-updated-t-sql.md)

#### <a name="subject-areas-which-have-no-new-or-recently-updated-articles"></a>Aree di interesse senza articoli nuovi o aggiornati di recente

- [Nuovo + aggiornato (0 + 0): documentazione di **Data Migration Assistant (DMA) per SQL Server**](../dma/new-updated-dma.md)
- [Nuovo + aggiornato (0+0): **ActiveX Data Objects (ADO) for SQL (ActiveX Data Objects (ADO) per SQL)** Docs](../ado/new-updated-ado.md)
- [Nuovo + aggiornato (0+0): **Data Quality Services for SQL (Data Quality Services per SQL)** Docs](../data-quality-services/new-updated-data-quality-services.md)
- [Nuovo + aggiornato (0+0): **Data Mining Extensions (DMX) for SQL (Estensioni di data mining (DMX) per SQL)** Docs](../dmx/new-updated-dmx.md)
- [Nuovo + aggiornato (0+0): documentazione di **Master Data Services (MDS) per SQL**](../master-data-services/new-updated-master-data-services.md)
- [Nuovo + aggiornato (0+0): **Multidimensional Expressions (MDX) for SQL(Espressioni MDX per SQL)** Docs](../mdx/new-updated-mdx.md)
- [Nuovo + aggiornato (0+0): **ODBC (Open Database Connectivity) for SQL (ODBC (Open Database Connectivity) per SQL)** Docs](../odbc/new-updated-odbc.md)
- [Nuovo + aggiornato (0+0): **PowerShell for SQL (PowerShell per SQL)** Docs](../powershell/new-updated-powershell.md)
- [Nuovo + aggiornato (0+0): documentazione degli **strumenti per SQL**](../tools/new-updated-tools.md)
- [Nuovo + aggiornato (0+0): **XQuery for SQL (XQuery per SQL)** Docs](../xquery/new-updated-xquery.md)


