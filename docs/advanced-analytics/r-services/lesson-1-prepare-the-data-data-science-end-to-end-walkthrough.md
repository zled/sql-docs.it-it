---
title: "Lezione 1: Preparare i dati (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: ""
ms.date: "03/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 65fd41d4-c94e-4929-a24a-20e792a86579
caps.latest.revision: 29
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 25
---
# Lezione 1: Preparare i dati (Procedura dettagliata end-to-end per l&#39;analisi scientifica dei dati)
Per prepararsi per questa procedura dettagliata, è necessario eseguire le operazioni seguenti:

1. Scaricare i dati e tutti gli script R usati nella procedura dettagliata. Viene fornito uno script di PowerShell per semplificare il download da GitHub.   

2. Installare alcuni pacchetti R aggiuntivi, sia nel server che nella workstation R.  

3. Preparare l'ambiente, tra cui il database e i dati usati per la modellazione e l'assegnazione dei punteggi.
 
    A tale scopo, si userà un secondo script di PowerShell, RunSQL_R_Walkthrough.ps1.
    Lo script configura il database e carica i dati nella tabella specificata.  Crea inoltre alcune funzioni e stored procedure SQL che semplificano le attività di analisi scientifica dei dati. 
 

## <a name="1-download-the-data-and-scripts"></a>1. Scaricare i dati e gli script  
Tutto il codice necessario per completare questa procedura dettagliata è disponibile in un repository GitHub. È possibile usare uno script di PowerShell per creare una copia locale dei file.  
  
#### <a name="to-download-all-scripts-using-powershell"></a>Per scaricare tutti gli script con PowerShell  
  
1.  Nel computer client per l'analisi scientifica dei dati, aprire un prompt dei comandi Windows PowerShell come amministratore.  
  
2.  Se PowerShell non è stato eseguito in precedenza su questa istanza o non è presente l'autorizzazione per l'esecuzione di script, potrebbe verificarsi un errore. In tal caso eseguire il comando che segue prima di eseguire lo script, per autorizzare temporaneamente gli script senza modificare i valori predefiniti di sistema.  
  
    ```  
    Set-ExecutionPolicy Unrestricted -Scope Process -Force  
    ```  
  
3.  Eseguire il comando seguente per scaricare i file di script in una directory locale. Se non si specifica una directory diversa, per impostazione predefinita viene creata la cartella C:\tempR e tutti i file vengono salvati in tale percorso.  
  
    ```  
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_R_Walkthrough.ps1'  
    $ps1_dest = "$pwd\Download_Scripts_R_Walkthrough.ps1"  
    $wc = New-Object System.Net.WebClient  
    $wc.DownloadFile($source, $ps1_dest)  
    .\Download_Scripts_R_Walkthrough.ps1 –DestDir 'C:\tempR'  
  
    ```  
  
    Per salvare i file in una directory diversa, modificare i valori del parametro *DestDir* e specificare una cartella del computer in uso diversa. Se si digita il nome di una cartella che non esiste, lo script di PowerShell creerà automaticamente la cartella.  
  
4.  Dopo il completamento del download la console dei comandi Windows PowerShell dovrebbe avere un aspetto simile al seguente:  
  
    ![After completion of PowerShell script](../../advanced-analytics/r-services/media/rsql-e2e-psscriptresults.PNG "After completion of PowerShell script")  
  
5.  Nella console di PowerShell è possibile eseguire il comando `ls` per visualizzare l'elenco dei file che sono stati scaricati in *DestDir*.  Per l'elenco e la descrizione dei file, vedere [Elementi inclusi nel download](#What-the-Download-Includes).
  
## <a name="2-install-required-packages"></a>2. Installare i pacchetti necessari  
Questa procedura dettagliata richiede alcune librerie R che non sono installate per impostazione predefinita come parte di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. È necessario installare tali pacchetti sia sul client nel quale si svilupperà la soluzione sia sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel quale si distribuirà la soluzione stessa.  
  
### <a name="install-required-packages-on-the-client"></a>Installare i pacchetti necessari nel client  
Lo script R scaricato include i comandi per scaricare e installare questi pacchetti.  
  
1.  Nell'ambiente R aprire il file script RSQL_R_Walkthrough.R.  
  
2.  Evidenziare ed eseguire le seguenti righe di codice.  
  
    ```  
    # Install required R libraries for this walkthrough if they are not installed.   
  
    if (!('ggmap' %in% rownames(installed.packages()))){  
      install.packages('ggmap')  
    }  
    if (!('mapproj' %in% rownames(installed.packages()))){  
      install.packages('mapproj')  
    }  
    if (!('ROCR' %in% rownames(installed.packages()))){  
      install.packages('ROCR')  
    }  
    if (!('RODBC' %in% rownames(installed.packages()))){  
      install.packages('RODBC')  
    }  
    ```  
  
### <a name="install-required-packages-on-the-server"></a>Installare i pacchetti necessari nel server  

  
1.  Nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aprire RGui.exe come amministratore.  Se SQL Server R Services è stato installato con le impostazioni predefinite, RGui.exe è disponibile in C:\Programmi\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\bin\x64.  
  
    In alternativa, se nel computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è stato installato un altro ambiente R (ad esempio RStudio), è possibile usare la console di R per eseguire i comandi.  
  
2.  Al prompt di R, eseguire i comandi R seguenti:  
  
    ```  
    install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])  
    install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1]) 
    install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1]) 
    install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1]) 
    ```  
  
**Note:**  
  
-   In questo esempio la funzione grep di R viene usata per cercare il vettore di percorsi disponibili e trovare quello presente in "Program Files". Per altre informazioni, vedere [http://www.rdocumentation.org/packages/base/functions/grep](http://www.rdocumentation.org/packages/base/functions/grep).   
  
-   Se si ritiene che i pacchetti siano già installati, controllare l'elenco dei pacchetti installati usando la funzione R `installed.packages()`.  
  
-   Se nel client non è possibile scrivere nella libreria principale in Programmi, è possibile eseguire l'installazione in una libreria utente. Tuttavia, quando si installano i pacchetti nel computer SQL Server, è necessario installarli della libreria predefinita usata da SQL Server R Services. Non usare una libreria utente. Per altre informazioni, vedere [Installing New R Packages on SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md) (Installazione di nuovi pacchetti R in SQL Server).
      

## <a name="3-run-powershell-script-runsqlrwalkthroughps1"></a>3. Eseguire lo script di PowerShell RunSQL_R_Walkthrough.ps1  

È possibile eseguire questo script di PowerShell nel computer in cui verrà compilata la soluzione, ad esempio il computer per sviluppare e testare il codice R. Il computer deve essere in grado di connettersi al computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con il protocollo Named Pipes.  
  
Lo script effettua le seguenti operazioni:  
  
-   Controlla se sono installati SQL Native Client e utilità della riga di comando di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Gli strumenti della riga di comando consentono di eseguire l' [utilità bcp](../../tools/bcp-utility.md)usata per il caricamento bulk rapido di dati nelle tabelle SQL.    
-   Si connette all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] specificata ed esegue alcuni script [!INCLUDE[tsql](../../includes/tsql-md.md)] per configurare il database e creare le tabelle per il modello e i dati.    
-   Esegue uno script SQL per creare varie stored procedure.    
-   Carica i dati scaricati in precedenza nella tabella nyctaxi_sample.    
-   Riscrive gli argomenti del file script R in modo che usino il nome del database specificato. 

### <a name="to-run-the-script"></a>Per eseguire lo script
  
1.  Aprire un prompt dei comandi PowerShell come amministratore.    
  
2.  Passare alla cartella in cui sono stati scaricati gli script e digitare il nome dello script, come indicato. Premere INVIO.  
  
    ```  
    .\RunSQL_R_Walkthrough.ps1  
    ```  
  
3.  Verranno richiesti i parametri seguenti:  
  
    - Nome del database da creare. 
      Ad esempio, è possibile digitare **Tutorial** o **Taxi**.  
    - Credenziali con cui eseguire lo script. Esistono due opzioni:
        + Digitare il nome di un account di accesso SQL con i privilegi CREATE DATABASE e specificare la password SQL in un successivo prompt dei comandi.
        + Premere INVIO senza digitare un nome per usare la propria identità Windows e al prompt protetto digitare la password di Windows. PowerShell non supporta l'immissione di un nome utente Windows diverso. 

          Se non si specifica un utente valido, lo script userà per impostazione predefinita l'autenticazione integrata di Windows.  
  
    -   Percorso completo del file csv da caricare nel database  
  
        Lo script deve scaricare il file e caricare i dati nel database in modo automatico, ma se l'operazione non riesce, è possibile caricare i dati manualmente.  
  
4.  Premere INVIO per eseguire lo script.  
  
## <a name="troubleshooting"></a>Risoluzione dei problemi  
 
 In caso di problemi è possibile eseguire alcuni o tutti i passaggi manualmente, usando le righe dello script PowerShell come esempi. 
 

### <a name="the-powershell-script-didnt-download-the-data"></a>Lo script di PowerShell non ha scaricato i dati
  
Per scaricare i dati manualmente, fare clic con il pulsante destro del mouse sul collegamento seguente e selezionare **Salva oggetto con nome**.  
  
[http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv](http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv)  
  
Annotare il percorso dei file di dati scaricato e del nome del file in cui sono stati salvati i dati. Il percorso sarà necessario per caricare i dati nella tabella mediante **bcp**.  
  
### <a name="i-was-unable-to-download-the-data"></a>Non è stato possibile scaricare i dati
Il file di dati è di grandi dimensioni. Usare un computer con una connessione Internet affidabile per evitare possibili timeout durante l'operazione di download.  

  
### <a name="could-not-connect-or-script-failed"></a>Non è stato possibile connettersi o lo script non è riuscito  
  
+ Controllare l'ortografia del nome dell'istanza. 
+ Verificare la stringa di connessione completa.    
+ A seconda dei requisiti della rete, è possibile che il nome dell'istanza vada qualificato con uno o più nomi di subnet.  Ad esempio, se MYSERVER non funziona, provare myserver.subnet.mycompany.com.
  
### <a name="network-error-or-protocol-not-found"></a>Errore di rete o protocollo non trovato  
  
+ Verificare che l'istanza supporti le connessioni remote.    
+ Verificare che l'utente SQL specificato sia in grado di connettersi in remoto al database e che Named Pipes sia abilitato per l'istanza.    
+ Controllare le autorizzazioni per l'account. L'account specificato potrebbe non avere le autorizzazioni per la creazione di un nuovo database e il caricamento dei dati.  

### <a name="bcp-did-not-run"></a>bcp non è stato eseguito  

+ Verificare che l' [utilità bcp](../../tools/bcp-utility.md) sia disponibile nel computer in uso. È possibile eseguire l'utilità bcp da una finestra di PowerShell o da un prompt dei comandi di Windows.
+ Se si verifica un errore, aggiungere il percorso dell'utilità bcp alla variabile di ambiente di sistema PATH e riprovare.  

### <a name="the-table-schema-was-created-but-there-is-no-data-in-the-table"></a>Lo schema della tabella è stato creato ma non sono presenti dati nella tabella

Se la parte restante dello script è stata eseguita senza problemi, è possibile caricare manualmente i dati nella tabella chiamando **bcp** dalla riga di comando come segue:  


 
**Uso di un account di accesso SQL**
    
~~~~ 
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U <SQL login> -P <password  
~~~~  
  
**Uso dell'autenticazione di Windows**  

~~~~
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -T 
~~~~ 
  
  
+ La parola chiave **in** specifica la direzione dello spostamento dati.  
+ L'argomento **-f** richiede di specificare il percorso completo di un file di formato. Un file di formato è necessario se si usa l'opzione **in**.
+ Usare gli argomenti **-U** e **-P** se esegue bcp con un account di accesso SQL.
+ Usare l'argomento **-T** se si usa l'autenticazione integrata di Windows. 

  
### <a name="how-can-i-run-the-script-without-prompts"></a>Come è possibile eseguire lo script senza prompt?  
  
È possibile specificare tutti i parametri in una singola riga di comando usando i valori specifici dell'ambiente. 
  
```  
.\RunSQL_R_Walkthrough.ps1 -server <server address> -dbname <new db name> -u <user name> -p <password> -csvfilepath <path to csv file>  
```  
  
Ad esempio, per eseguire lo script con un account di accesso SQL:  
  
```  
.\RunSQL_R_Walkthrough.ps1 -server MyServer.subnet.domain.com -dbname MyDB –u SqlUserName –p SqlUsersPassword -csvfilepath C:\temp\nyctaxi1pct.csv  
```  
  
In questo esempio vengono eseguite le operazioni seguenti:  
  
-   Connessione all'istanza e al database specificati mediante le credenziali di *SqlUserName*.  
-   Recupero dei dati dal file *C:\temp\nyctaxi1pct.csv*.  
-   Caricamento dei dati nella tabella *dbo.nyctaxi_sample*, nel database *MyDB* dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] denominata *MyServer*.  

### <a name="the-data-loaded-but-it-contains-duplicates"></a>I dati sono stati caricati ma contengono duplicati

Se è già presente una tabella esistente con lo schema corretto, l'esecuzione di bcp continua, ma verrà inserita una nuova copia dei dati anziché sovrascrivere i dati esistenti. Ciò darà origine a dati duplicati.  Assicurarsi di troncare le tabelle esistenti prima di eseguire nuovamente lo script.

## <a name="what-the-download-includes"></a>Elementi inclusi nel download

Quando si scaricano i file dal repository GitHub, si otterrà quanto segue:
+ Dati in formato CSV
+ Uno script di PowerShell per la preparazione dell'ambiente
+ Un file di formato XML per l'importazione dei dati in SQL Server tramite bcp
+ Più script T-SQL
+ Tutto il codice R necessario eseguire questa procedura dettagliata

### <a name="training-and-scoring-data"></a>Dati di training e dei punteggi  
I dati sono un campione rappresentativo del set di dati dei taxi di New York City, contenente record di oltre 173 milioni di corse singole effettuate nel 2013, inclusi gli importi delle corse e delle mance corrisposte per ogni corsa.  Per altre informazioni su come tali dati sono stati raccolti in origine e su come ottenere il set di dati completo, vedere  
[http://chriswhong.com/open-data/foil_nyc_taxi/](http://chriswhong.com/open-data/foil_nyc_taxi/).  
  
Per semplificare la manipolazione, il team di analisi scientifica dei dati Microsoft ha eseguito un downsampling per ottenere solo l'1% dei dati.  Tali dati sono stati quindi condivisi in un contenitore di archiviazione BLOB pubblico di Azure, in formato csv. I dati di origine sono inclusi in un file non compresso, con dimensioni di poco inferiori a 350 MB.  
 
### <a name="files"></a>File

 
+ **RunSQL_R_Walkthrough.ps1** Per iniziare si eseguirà questo script usando PowerShell. Lo script chiama gli script SQL per il caricamento di dati nel database.  
    
+ **taxiimportfmt.xml** File di definizione formato mediante il quale l'utilità BCP carica dati nel database.
      
+ **RSQL_R_Walkthrough.R** Questo è lo script R di base che verrà usato nel resto delle lezioni per eseguire l'analisi dei dati e la modellazione. Include tutto il codice R necessario per esplorare i dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , compilare il modello di classificazione e creare tracciati.   
  
### <a name="sql-scripts"></a>Script SQL  
Questo script PowerShell esegue più script [!INCLUDE[tsql](../../includes/tsql-md.md)] nel server. La tabella seguente elenca i file script [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
|Nome file script SQL|Funzione|  
|------------------------|----------------|  
|create-db-tb-upload-data.sql|Crea un database e due tabelle:<br /><br /> *nyctaxi_sample*: tabella in cui vengono archiviati i dati di training, ovvero il campione corrispondente all'1% del set di dati dei taxi di New York City. La tabella è provvista di un indice columnstore cluster per migliorare le prestazioni di archiviazione e query.<br /><br /> *nyc_taxi_models*: tabella vuota da usare in un secondo momento per salvare il modello di classificazione sottoposto a training.|  
|PredictTipBatchMode.sql|Crea una stored procedure che chiama un modello sottoposto a training per prevedere le etichette delle nuove osservazioni. Accetta come parametro di input una query.|  
|PredictTipSingleMode.sql|Crea una stored procedure che chiama un modello di classificazione sottoposto a training per prevedere le etichette delle nuove osservazioni. Le variabili delle nuove osservazioni vengono passate come parametri inline.|  
|PersistModel.sql|Crea una stored procedure che consente di archiviare la rappresentazione binaria del modello di classificazione in una tabella del database.|  
|fnCalculateDistance.sql|Crea una funzione SQL con valori scalari che calcola la distanza diretta tra le posizioni di inizio corsa e fine corsa.|  
|fnEngineerFeatures.sql|Crea una funzione con valori di tabella SQL che definisce le funzionalità per il training del modello di classificazione|  
  
Tutte le query SQL che vengono usate in questa procedura dettagliata sono state testate e possono essere eseguite senza modifiche nel codice R. Se tuttavia si vuole sperimentare ulteriormente o sviluppare soluzioni personalizzate mediante query SQL, è consigliabile usare un ambiente di sviluppo come [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per testare e ottimizzare le query prima di aggiungerle al codice R.  
  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 2: Visualizzare ed esplorare i dati &#40;Procedura dettagliata end-to-end per l'analisi scientifica dei dati&#41;](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Lezione precedente  
[Procedura dettagliata end-to-end per l'analisi scientifica dei dati](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)  
  
  
  
