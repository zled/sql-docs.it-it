---
title: Preparare i dati di utilizzo di PowerShell (procedura dettagliata) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 65fd41d4-c94e-4929-a24a-20e792a86579
caps.latest.revision: 30
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e1d85684da36ef69caf9dfa39f155a320def37b5
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="prepare-the-data-using-powershell-walkthrough"></a>Preparare i dati di utilizzo di PowerShell (procedura dettagliata)

A questo punto, è necessario disporre di uno dei seguenti installati:

+ SQL Server 2016 R Services
+ Servizi SQL Server 2017 Machine Learning, con il linguaggio R abilitato

In questa lezione si scarica i dati, i pacchetti R e gli script R utilizzati nella procedura dettagliata da un repository di Github. È possibile scaricare tutti gli elementi usando uno script di PowerShell per praticità.

È inoltre necessario installare alcuni pacchetti R aggiuntivi, nel server e nella workstation di R. Vengono descritti i passaggi.

È quindi possibile utilizzare uno script di PowerShell secondo, RunSQL_R_Walkthrough.ps1, per configurare il database utilizzato per la modellazione e assegnazione dei punteggi. Script eseguiti da un caricamento bulk dei dati nel database si specificano e quindi crea alcune funzioni SQL e stored procedure che semplificano le attività di analisi scientifica dei dati.

Iniziamo!

## <a name="1-download-the-data-and-scripts"></a>1. Scaricare i dati e gli script

Tutto il codice necessario è stato specificato in un repository di GitHub. È possibile usare uno script di PowerShell per creare una copia locale dei file.

1.  Nel computer client per l'analisi scientifica dei dati, aprire un prompt dei comandi Windows PowerShell come amministratore.

2.  Per assicurarsi di poter eseguire lo script di download senza errori, eseguire questo comando. Il comando consente temporaneamente gli script senza modificare le impostazioni predefinite di sistema.

    ```
    Set-ExecutionPolicy Unrestricted -Scope Process -Force
    ```
      
3.  Eseguire il comando di PowerShell seguente per scaricare i file di script in una directory locale. Se non si specifica una directory diversa, per impostazione predefinita la cartella `C:\tempR` viene creata e tutti i file salvati in tale posizione.
  
    ```
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_R_Walkthrough.ps1'  
    $ps1_dest = "$pwd\Download_Scripts_R_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_R_Walkthrough.ps1 –DestDir 'C:\tempR'
    ```
  
    Per salvare i file in una directory diversa, modificare i valori del parametro *DestDir* e specificare una cartella del computer in uso diversa. Se si digita un nome di cartella non esiste, lo script di PowerShell crea la cartella per l'utente.
  
4.  Il download potrebbe richiedere alcuni minuti. Dopo il completamento, la console dei comandi di Windows PowerShell dovrebbe avere un aspetto simile al seguente:
  
    ![Dopo il completamento dello script di PowerShell](media/rsql-e2e-psscriptresults.PNG "Dopo il completamento dello script di PowerShell")
  
5.  Nella console di PowerShell è possibile eseguire il comando `ls` per visualizzare l'elenco dei file che sono stati scaricati in *DestDir*.  Per una descrizione dei file, vedere [cosa è incluso](#What-the-Download-Includes).

## <a name="2-install-required-r-packages"></a>2. Installare pacchetti R richiesti

Questa procedura dettagliata richiede alcune librerie R che non sono installate per impostazione predefinita come parte di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. È necessario installare i pacchetti nel client in cui si sviluppa la soluzione e sul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer in cui si distribuisce la soluzione.

### <a name="install-required-packages-on-the-client"></a>Installare i pacchetti necessari nel client

Lo script R scaricato include i comandi per scaricare e installare questi pacchetti.

1. Nell'ambiente R aprire il file script RSQL_R_Walkthrough.R.

2. Evidenziare ed eseguire le seguenti righe di codice.
    
    ```
    # Install required R libraries, if they are not already installed.
    if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
    if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
    if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
    if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
    ```
    
    Inoltre, alcuni pacchetti installare pacchetti richiesti. In tutto sono necessari circa 32 pacchetti.

### <a name="install-required-packages-on-the-server"></a>Installare i pacchetti necessari nel server

Esistono molti modi diversi, che è possibile installare i pacchetti in SQL Server. Ad esempio, SQL Server fornisce un [pacchetto gestione](../r/installing-and-managing-r-packages.md) funzionalità che consente agli amministratori di database, creare un repository di pacchetti e assegnare utente i diritti per installare i propri pacchetti. Tuttavia, se si è un amministratore del computer, è possibile installare nuovi pacchetti tramite R, fino a quando si installa per la libreria corretta.

> [!NOTE]
> Nel server, **non** installare in una raccolta di utenti, anche se viene richiesto. Se si installa una libreria di utente, l'istanza di SQL Server non è possibile trovare o eseguire i pacchetti. Per altre informazioni, vedere [Installing New R Packages on SQL Server](../r/install-additional-r-packages-on-sql-server.md)(Installazione di nuovi pacchetti R in SQL Server).

1. Nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aprire RGui.exe **come amministratore**.  Se SQL Server R Services è stato installato con le impostazioni predefinite, RGui.exe è disponibile in C:\Programmi\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64.

2.  Al prompt di R, eseguire i comandi R seguenti:
  
    ```
    install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
    ```

    - In questo esempio la funzione grep di R viene usata per cercare il vettore di percorsi disponibili e trovare quello presente in "Program Files". Per altre informazioni, vedere [http://www.rdocumentation.org/packages/base/functions/grep](http://www.rdocumentation.org/packages/base/functions/grep).

    - Se si ritiene che i pacchetti sono già installati, controllare l'elenco dei pacchetti installati eseguendo `installed.packages()`.

## <a name="3-prepare-the-environment-using-runsqlrwalkthroughps1"></a>3. Preparare l'ambiente utilizzando RunSQL_R_Walkthrough.ps1

Con il file di dati, gli script R e gli script T-SQL, il download include lo script di PowerShell `RunSQL_R_Walkthrough.ps1`. Lo script effettua le seguenti operazioni:

- Controlla se sono installati SQL Native Client e utilità della riga di comando di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Gli strumenti da riga di comando sono necessari per eseguire l'[utilità bcp](../../tools/bcp-utility.md), usata per il caricamento bulk rapido dei dati nelle tabelle SQL.

- Si connette all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificata ed esegue alcuni script [!INCLUDE[tsql](../../includes/tsql-md.md)] per configurare il database e creare le tabelle per il modello e i dati.

- Esegue uno script SQL per creare varie stored procedure.

- Carica i dati scaricati in precedenza in una tabella denominata `nyctaxi_sample`.

- Riscrive gli argomenti del file script R in modo che usino il nome del database specificato.

È consigliabile eseguire questo script nel computer in cui si compila la soluzione: ad esempio, il computer portatile in cui sviluppare e testare il codice R. Questo computer, che verrà chiamato client di data science, deve essere in grado di connettersi al computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con il protocollo Named Pipes.

1. Aprire una riga di comando di PowerShell **come amministratore**.
  
2.  Passare alla cartella in cui sono stati scaricati gli script e digitare il nome dello script, come indicato. Premere INVIO.

    ```
    .\RunSQL_R_Walkthrough.ps1
    ```
  
3.  Richiesto per ognuno dei parametri seguenti:
  
    **Nome del server database**: il nome dell'istanza di SQL Server in cui è installato Machine learning Services o R Services.

    A seconda dei requisiti della rete, è possibile che il nome dell'istanza vada qualificato con uno o più nomi di subnet.  Ad esempio, se MYSERVER non funziona, provare myserver.subnet.mycompany.com.
    
    **Nome del database da creare**: è ad esempio possibile digitare **Esercitazione** o **Taxi**

    **Nome utente**: specificare un account con privilegi di accesso ai database. Esistono due opzioni:
    
    + Digitare il nome di un account di accesso SQL con i privilegi CREATE DATABASE e specificare la password SQL in un successivo prompt dei comandi.
    + Premere INVIO senza digitare un nome per usare la propria identità Windows e al prompt protetto digitare la password di Windows. PowerShell non supporta l'immissione di un nome utente Windows diverso.
    + Se non è possibile specificare un utente valido, per impostazione predefinita lo script utilizzando l'autenticazione integrata di Windows.
    
      > [!WARNING]
      > Quando si usa il prompt dei comandi nello script di PowerShell per fornire le credenziali, la password viene scritto il file di script aggiornato in testo normale. Modificare il file per rimuovere le credenziali immediatamente dopo aver creato gli oggetti R necessari.
      
    **Percorso del file CSV**: specificare il percorso completo del file di dati. Il percorso e il nome file predefinito sono `C:\tempR\nyctaxi1pct.csv1`.
  
4.  Premere INVIO per eseguire lo script.

    Lo script dovrebbe scaricare il file e caricare i dati nel database automaticamente. L'operazione può richiedere un po' di tempo. Controllare i messaggi di stato nella finestra di PowerShell.
      
    Se l'importazione o qualsiasi altro passaggio si verifica un errore, è possibile caricare i dati manualmente come descritto nel [Troubleshooting](#bkmk_Troubleshooting) sezione.

**Risultati (completamento corretto)**

```
Execution successful
Completed registering all stored procedures used in this walkthrough.
This step (registering all stored procedures) takes 0.39 seconds.
Plug in the database server name, database name, user name and password into the R script file
This step (plugging in database information) takes 0.48 seconds.
```

Fare clic su questo collegamento per passare alla lezione successiva: [visualizzare ed esplorare i dati di utilizzo di SQL](/walkthrough-view-and-explore-the-data.md)

## <a name="bkmk_Troubleshooting"></a>Risoluzione dei problemi

Se si verificano problemi con lo script di PowerShell, è possibile eseguire alcuni o tutti i passaggi manualmente, utilizzando le righe dello script PowerShell come esempi. In questa sezione sono elencati alcuni problemi comuni e soluzioni alternative.

### <a name="powershell-script-didnt-download-the-data"></a>Lo script di PowerShell non ha scaricato i dati

Per scaricare i dati manualmente, fare clic con il pulsante destro del mouse sul collegamento seguente e selezionare **Salva oggetto con nome**.

[http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv](http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv)

Annotare il percorso dei file di dati scaricato e del nome del file in cui sono stati salvati i dati. È necessario il percorso completo per caricare i dati per la tabella usando **bcp**.

### <a name="unable-to-download-the-data"></a>Non è stato possibile scaricare i dati

Il file di dati è di grandi dimensioni. È necessario utilizzare un computer che dispone di una connessione Internet relativamente buona o il download potrebbe scadere.

### <a name="could-not-connect-or-script-failed"></a>Non è stato possibile connettersi o lo script non è riuscito

Questo errore potrebbe verificarsi quando si esegue uno degli script: *Si è verificato un errore specifico dell'istanza o relativo alla rete durante il tentativo di stabilire una connessione a SQL Server*

+ Controllare l'ortografia del nome dell'istanza.
+ Verificare la stringa di connessione completa.
+ A seconda dei requisiti della rete, è possibile che il nome dell'istanza vada qualificato con uno o più nomi di subnet.  Ad esempio, se MYSERVER non funziona, provare myserver.subnet.mycompany.com.
+ Verificare se Windows Firewall consente le connessioni da SQL Server.
+ Provare a registrare il server e assicurarsi che consenta le connessioni remote.
+ Se si usa un'istanza denominata, abilitare SQL Browser semplificare le connessioni.

### <a name="network-error-or-protocol-not-found"></a>Errore di rete o protocollo non trovato

+ Verificare che l'istanza supporti le connessioni remote.
+ Verificare che l'utente SQL specificato possa connettersi in remoto al database.
+ Abilitare il protocollo Named Pipes nell'istanza.
+ Controllare le autorizzazioni per l'account. L'account specificato potrebbe non avere le autorizzazioni per la creazione di un nuovo database e il caricamento dei dati.

### <a name="bcp-did-not-run"></a>bcp non è stato eseguito

+ Verificare che l' [utilità bcp](../../tools/bcp-utility.md) sia disponibile nel computer in uso. È possibile eseguire **bcp** da una finestra di PowerShell o da un prompt dei comandi di Windows.
+ Se si verifica un errore, aggiungere il percorso dell'utilità **bcp** alla variabile di ambiente di sistema PATH e riprovare.

### <a name="the-table-schema-was-created-but-the-table-has-no-data"></a>Lo schema della tabella è stato creato ma la tabella non contiene dati

Se la parte restante dello script è stata eseguita senza problemi, è possibile caricare manualmente i dati nella tabella chiamando **bcp** dalla riga di comando come segue:

#### <a name="using-a-sql-login"></a>Uso di un account di accesso SQL

~~~~
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U <SQL login> -P <password>
~~~~

#### <a name="using-windows-authentication"></a>Uso dell'autenticazione di Windows

~~~~
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -T
~~~~

+ Il `in` parola chiave specifica la direzione di spostamento dei dati.
+ L'argomento  **-f** richiede di specificare il percorso completo di un file di formato. Un file di formato è necessario se si usa l'opzione **in** .
+ Usare gli argomenti **-U** e **-P** se esegue bcp con un account di accesso SQL.
+ Usare l'argomento **-T** se si usa l'autenticazione integrata di Windows.

Se lo script non carica i dati, controllare la sintassi e verificare che il nome del server sia specificato correttamente per la rete. Assicurarsi ad esempio di includere eventuali subnet e il nome del computer se ci si connette a un'istanza denominata. Verificare che l'account di accesso ha la possibilità di eseguire il caricamento bulk.

### <a name="i-want-to-run-the-script-without-prompts"></a>Si vuole eseguire lo script senza prompt

È possibile specificare tutti i parametri in una singola riga di comando, usando questo modello, con valori specifici dell'ambiente.

```
.\RunSQL_R_Walkthrough.ps1 -server <server address> -dbname <new db name> -u <user name> -p <password> -csvfilepath <path to csv file>
```

L'esempio seguente esegue lo script usando account di accesso SQL:

```
.\RunSQL_R_Walkthrough.ps1 -server MyServer.subnet.domain.com -dbname MyDB –u SqlUserName –p SqlUsersPassword -csvfilepath C:\temp\nyctaxi1pct.csv
```

-   Connessione all'istanza e al database specificati mediante le credenziali di *SqlUserName*.
-   Recupero dei dati dal file *C:\temp\nyctaxi1pct.csv*.
-   Caricamento dei dati nella tabella *dbo.nyctaxi_sample*, nel database *MyDB* dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] denominata *MyServer*.

### <a name="the-data-loaded-but-it-contains-duplicates"></a>I dati sono stati caricati ma contengono duplicati

Se il database contiene una tabella esistente dello stesso nome e lo stesso schema, **bcp** inserisce una nuova copia di dati anziché la sovrascrittura di dati esistenti.

Per evitare dati duplicati, troncare le tabelle esistenti prima di eseguire nuovamente lo script.

## <a name="whats-included-in-the-sample"></a>Cosa è incluso nell'esempio

Quando si scaricano i file dal repository GitHub, si ottiene quanto segue:

+ Dati in formato CSV. vedere [Training e assegnazione dei punteggi dati](#bkmk_data) per informazioni dettagliate
+ Uno script di PowerShell per la preparazione dell'ambiente
+ Un file di formato XML per l'importazione dei dati in SQL Server tramite bcp
+ Più script T-SQL
+ Tutto il codice R necessario eseguire questa procedura dettagliata

### <a name="bkmk_data"></a>Set di training e di assegnare punteggi ai dati

I dati sono un campione rappresentativo del set di dati dei taxi di New York City, contenente record di oltre 173 milioni di corse singole effettuate nel 2013, inclusi gli importi delle corse e delle mance corrisposte per ogni corsa. Per semplificare la manipolazione, il team di analisi scientifica dei dati Microsoft ha eseguito un downsampling per ottenere solo l'1% dei dati.  Tali dati sono stati quindi condivisi in un contenitore di archiviazione BLOB pubblico di Azure, in formato csv. I dati di origine sono inclusi in un file non compresso, con dimensioni di poco inferiori a 350 MB.

+ Set di dati pubblici: [NYC Taxi e Commissione Limousine] (http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)

+ [La creazione di modelli di Azure ML nel set di dati NYC Taxi] (https://blogs.technet.microsoft.com/machinelearning/2015/04/02/building-azure-ml-models-on-the-nyc-taxi-dataset/.

### <a name="powershell-and-r-script-files"></a>File di script di PowerShell e R

+ **RunSQL_R_Walkthrough.ps1** si esegue lo script in primo luogo, usando PowerShell. Lo script chiama gli script SQL per il caricamento di dati nel database.

+ **taxiimportfmt.xml** File di definizione formato mediante il quale l'utilità BCP carica dati nel database.

+ **RSQL_R_Walkthrough.R** script di base R che viene utilizzato nel resto delle lezioni per eseguire l'analisi dei dati e modellazione. Include tutto il codice R necessario per esplorare i dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , compilare il modello di classificazione e creare tracciati.

### <a name="t-sql-script-files"></a>File di script T-SQL

Lo script di PowerShell esegue più [!INCLUDE[tsql](../../includes/tsql-md.md)] script nell'istanza di SQL Server. La tabella seguente elenca i [!INCLUDE[tsql](../../includes/tsql-md.md)] script e le operazioni eseguite.

|Nome file script SQL|Description|
|------------------------|----------------|
|create-db-tb-upload-data.sql|Crea un database e due tabelle:<br /><br /> *nyctaxi_sample*: tabella in cui vengono archiviati i dati di training, ovvero il campione corrispondente all'1% del set di dati dei taxi di New York City. La tabella è provvista di un indice columnstore cluster per migliorare le prestazioni di archiviazione e query.<br /><br /> *nyc_taxi_models*: tabella vuota da usare in un secondo momento per salvare il modello di classificazione sottoposto a training.|
|PredictTipBatchMode.sql|Crea una stored procedure che chiama un modello sottoposto a training per prevedere le etichette delle nuove osservazioni. Accetta come parametro di input una query.|
|PredictTipSingleMode.sql|Crea una stored procedure che chiama un modello di classificazione sottoposto a training per prevedere le etichette delle nuove osservazioni. Le variabili delle nuove osservazioni vengono passate come parametri inline.|
|PersistModel.sql|Crea una stored procedure che consente di archiviare la rappresentazione binaria del modello di classificazione in una tabella del database.|
|fnCalculateDistance.sql|Crea una funzione SQL con valori scalari che calcola la distanza diretta tra le posizioni di inizio corsa e fine corsa.|
|fnEngineerFeatures.sql|Crea una funzione con valori di tabella SQL che definisce le funzionalità per il training del modello di classificazione|

Le query T-SQL utilizzate in questa procedura dettagliata sono state testate e possono essere eseguite come-dipende dal codice R. Se tuttavia si vuole sperimentare ulteriormente o sviluppare soluzioni personalizzate, è consigliabile usare un ambiente di sviluppo SQL dedicato per testare e ottimizzare le query prima di aggiungerle al codice R.

+ L'[estensione mssql](https://code.visualstudio.com/docs/languages/tsql) per [Visual Studio Code](https://code.visualstudio.com/) è un ambiente gratuito e leggero per l'esecuzione di query, che supporta anche la maggior parte delle attività di sviluppo di database.
+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) è uno strumento potente ma gratuito fornito per lo sviluppo e la gestione dei database di SQL Server.

## <a name="next-lesson"></a>Lezione successiva

[Visualizzare ed esplorare i dati con R e SQL](/walkthrough-view-and-explore-the-data.md)

## <a name="previous-lesson"></a>Lezione precedente

[Procedura dettagliata di analisi scientifica dei dati end-to-end per R e SQL Server](/walkthrough-data-science-end-to-end-walkthrough.md)

[Prerequisiti per la procedura dettagliata dell'analisi scientifica dei dati](walkthrough-prerequisites-for-data-science-walkthroughs.md)

