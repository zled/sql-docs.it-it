---
title: "Nuovi componenti in SQL Server per supportare i servizi di R | Microsoft Docs"
ms.custom: ""
ms.date: "06/03/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54e9ef3f-1136-471e-865a-7cf013673186
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 9
---
# Nuovi componenti in SQL Server per supportare i servizi di R

[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] include nuovi componenti, forniti dal [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] motore di database che supportano l'estensibilità per il linguaggio R. La protezione per questi componenti viene gestita da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e verrà descritto in dettaglio più avanti.

## I provider e nuovi componenti di SQL Server

Oltre alle shell che carica R ed esegue codice R come descritto nella panoramica dell'architettura, [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] include i componenti aggiuntivi.

### **Finestra di avvio** 
  Il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] è un nuovo servizio fornito da [!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)] per supportare l'esecuzione di script esterni, allo stesso modo in cui il servizio di indicizzazione e query full-text avvia un host separato per l'elaborazione di query full-text. 
  
  Tale servizio verrà avviato solo attendibile avvio che vengono pubblicati da Microsoft o che sono stati certificati da Microsoft come requisiti per la gestione delle prestazioni delle risorse. In [!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)], R è attualmente il solo linguaggio supportato da di [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)].
  
  Il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio viene eseguito con il proprio account utente. Ogni processo satellite per un linguaggio specifico di runtime erediterà l'account utente della finestra di avvio. Per ulteriori informazioni sulla configurazione e il contesto di sicurezza della finestra di avvio, vedere [Cenni preliminari sulla sicurezza](../../advanced-analytics/r-services/security-overview-sql-server-r-services.md).

### **BxlServer e Satellite SQL**
  BxlServer è un eseguibile fornito da Microsoft che gestisce la comunicazione tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e il runtime R e implementa le funzioni di ridimensionamento. Crea gli oggetti di processo di Windows che vengono utilizzati per contenere le sessioni di R, disposizioni sicuro le cartelle di lavoro per ogni processo R e utilizza SQL Satellite per gestire il trasferimento dei dati tra R e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].  

  In effetti, BxlServer è correlato a R che funziona con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] per supportare l'integrazione di R con SQL Server. BXL è l'acronimo di linguaggio Exchange binario e fa riferimento al formato dei dati utilizzato per spostare i dati in modo efficiente tra SQL Server e processi esterni, ad esempio R. 

 Satellite SQL è una nuova API di estendibilità in SQL Server 2016 fornito dal motore di database per supportare il codice esterno o Runtime esterni implementati utilizzando C o C++. R è attualmente l'unico runtime supportato. BxlServer utilizza Satellite SQL per la comunicazione con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
 
  Satellite SQL utilizza un formato di dati personalizzato che è ottimizzato per il trasferimento di dati rapido tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e linguaggi di script esterni. Esegue conversioni di tipi e definisce gli schemi dei set di dati di input e output durante le comunicazioni tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e r.

  BxlServer utilizza Satellite SQL per eseguire queste attività: 
  - Lettura di dati di input
  - Scrittura di dati di output
  - Argomenti di input
  - Scrittura degli argomenti di output
  - Gestione degli errori
  - Scrittura di STDOUT e STDERR nel client

  Satellite SQL può essere monitorato utilizzando gli eventi estesi. Per ulteriori informazioni, vedere [eventi estesi per i servizi di SQL Server R](../../advanced-analytics/r-services/extended-events-for-sql-server-r-services.md).


## I canali di comunicazione tra componenti

+ **TCP/IP** per impostazione predefinita, le comunicazioni interne tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e Satellite SQL utilizzare TCP/IP.

+ **Named Pipe**

  Trasferimento dei dati interna tra il BxlServer e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] tramite Satellite SQL utilizza un formato dati compressi di proprietari per migliorare le prestazioni. Dati dalla memoria R BxlServer vengono scambiati tramite named pipe nel formato BXL. 
  
+ **ODBC** le comunicazioni tra i client di analisi scientifica dei dati esterni e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza utilizzare ODBC. L'account che invia R processi per [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] deve disporre di entrambe le autorizzazioni per connettersi all'istanza ed eseguire script esterni. Inoltre, l'account deve disporre dell'autorizzazione per accedere ai dati utilizzati dal processo, per scrivere i dati (ad esempio, se il salvataggio dei risultati in una tabella) oppure per creare oggetti di database (ad esempio, se salvare funzioni R come parte di una nuova stored procedure).

  Quando [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] viene utilizzato come il contesto di calcolo per un processo di R inviato da un client remoto e il comando R deve recuperare dati da un'origine esterna, ODBC viene utilizzato per il writeback. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] verrà associare l'identità dell'utente che invia il comando R remoto per l'identità dell'utente nell'istanza corrente, eseguire il comando ODBC utilizzando le credenziali dell'utente. La stringa di connessione necessaria per eseguire questa chiamata ODBC viene ottenuta dal codice client.
  
  Possono essere effettuate altre chiamate ODBC nello script tramite **RODBC**. RODBC è un pacchetto R più diffusi utilizzato per accedere ai dati in database relazionali. Tuttavia, le prestazioni sono generalmente più provider confrontabili utilizzati da lenta [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Molti script R usano incorporate le chiamate a RODBC come modalità di recupero "secondario" set di dati da utilizzare nelle analisi. Ad esempio, la stored procedure che esegue il training di un modello potrebbe definire una query SQL per ottenere i dati di training di un modello, ma utilizzare una chiamata RODBC incorporata per ottenere alcuni fattori aggiuntivi, di eseguire ricerche o per ottenere nuovi dati da origini esterne, ad esempio Excel o file di testo.

  Il codice seguente viene illustrata una chiamata RODBC incorporata in uno script R:
   ~~~~
  library(RODBC);
  connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
  dbhandle <- odbcDriverConnect(connStr)
  OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
  ~~~~

+ **Altri protocolli** processi che potrebbe essere necessario lavorare in "blocchi" o trasferire i dati a un client remoto consente inoltre di. XDF formato supportato da Microsoft R. effettivo trasferimento dei dati è tramite BLOB codificato.

## Interazione dei componenti

L'architettura del componente descritto in precedenza è stato fornito per garantire che codice R open source può essere "così com'è", mentre fornendo notevolmente il miglioramento delle prestazioni per il codice che viene eseguito in un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer. Il meccanismo di interagiscono tra i componenti con il runtime di R e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] motore di database è diversa, a seconda della modalità di avvio il codice R. In questa sezione sono riepilogati gli scenari principali. 
 
### Script R eseguiti da SQL Server (database)

Codice R che viene eseguito da "interno" [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] viene eseguita chiamando una stored procedure. Pertanto, qualsiasi applicazione che è possibile eseguire una stored procedure chiamata può iniziare l'esecuzione di codice R.  In seguito [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] gestisce l'esecuzione di codice R, come riepilogato nel diagramma seguente.

![rsql_indb780-01](../../advanced-analytics/r-services/media/rsql-indb780-01.png)

1. Una richiesta per il runtime di R è indicata dal parametro _@language = 'R'_ passato alla stored procedure, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Invia la richiesta al servizio di avvio.
2. Il servizio Launchpad avvia l'utilità di avvio appropriato; In questo caso, RLauncher.
3. RLauncher avvia il processo di R esterno.
4. Coordinate BxlServer con il runtime R per gestire gli scambi di dati con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e l'archiviazione dei risultati di lavoro.
5. Nel sistema, Satellite SQL gestisce le comunicazioni sulle attività correlate e i processi con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
6. BxlServer utilizza Satellite SQL per comunicare lo stato e i risultati a [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
7. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Ottiene i risultati e chiude i processi e attività correlate. 


### Script R eseguiti da un client remoto

Durante la connessione da un client di analisi scientifica dei dati remota che supporta Microsoft R, è possibile eseguire funzioni R nel contesto di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] utilizzando le funzioni di ridimensionamento. Questo è un flusso di lavoro diverso da quello precedente e viene riepilogato nel diagramma seguente.


![rsql_fromR2db-01](../../advanced-analytics/r-services/media/rsql-fromr2db-01.png)

1. Per le funzioni di ridimensionamento, il runtime R chiama una funzione di collegamento che a sua volta chiama BxlServer. 
2. BxlServer viene fornito con Microsoft R e viene eseguito in un processo separato dalla fase di esecuzione R.
3. BxlServer determina la destinazione della connessione e avvia una connessione tramite ODBC, passando le credenziali fornite come parte della stringa di connessione nell'oggetto di origine di dati R.
4. BxlServer apre una connessione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza.
5. Per una chiamata a R, la finestra di avvio servizio viene richiamato, che è attiva, viene avviato il servizio di avvio appropriato, RLauncher. Successivamente, l'elaborazione del codice R è simile al processo per l'esecuzione di codice R da T-SQL.
6. RLauncher effettua una chiamata all'istanza del runtime R che è installato il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer. 
7. I risultati vengono restituiti BxlServer.
8. Satellite SQL gestisce la comunicazione con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e la pulitura degli oggetti processo correlato.
9. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] passa i risultati al client.

## Vedere anche
[Panoramica dell'architettura](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)
