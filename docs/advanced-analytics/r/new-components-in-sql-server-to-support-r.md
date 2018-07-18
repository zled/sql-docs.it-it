---
title: Componenti di SQL Server per il supporto di R | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: fa29a924b34bbe5737a89f5b111c92053b62d36b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203613"
---
# <a name="components-in-sql-server-to-support-r"></a>Componenti di SQL Server per il supporto di R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In SQL Server 2016 e 2017, il motore di database include i componenti facoltativi che supportano l'estensibilità per i linguaggi di script esterni, tra R e Python. È stato aggiunto il supporto per il linguaggio R in SQL Server 2016; il supporto per Python è stato aggiunto in servizi di SQL Server 2017 Machine Learning.

In questo argomento vengono descritti i nuovi componenti che funzionano in modo specifico con il linguaggio R. Per informazioni sul funzionamento di questi componenti con R open source, vedere [interoperabilità R](r-interoperability-in-sql-server.md)

## <a name="components-and-providers"></a>Provider e componenti

Oltre alla shell che carica R ed esegue codice R come descritto nella panoramica dell'architettura, [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] include i componenti aggiuntivi seguenti.

### <a name="launchpad"></a>Launchpad 

Il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] è un servizio fornito da [!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)] per supportare l'esecuzione di script esterni, allo stesso modo in cui il servizio di indicizzazione e query full-text avvia un host separato per l'elaborazione delle query full-text.

Il servizio Launchpad avvia solo utilità di avvio attendibili pubblicate da Microsoft o che Microsoft ha certificato come conformi ai requisiti di prestazioni e gestione delle risorse. I nomi per l'avvio di specifiche della lingua è semplici:

  + R - RLauncher.dll
  + Python - PythonLauncher.dll

Il servizio [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] viene eseguito con il relativo account utente. Ogni processo satellite per il runtime di un linguaggio specifico eredita l'account utente di Launchpad. Per ulteriori informazioni sulla configurazione e il contesto di sicurezza della finestra di avvio, vedere [Cenni preliminari sulla sicurezza](../../advanced-analytics/r/security-overview-sql-server-r.md).

### <a name="bxlserver-and-sql-satellite"></a>BxlServer e Satellite SQL

BxlServer è un eseguibile fornito da Microsoft che gestisce la comunicazione tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e il runtime di R e implementa le funzioni RevoScaleR. Crea gli oggetti processo di Windows usati per contenere le sessioni di R, effettua il provisioning di cartelle di lavoro sicure per ogni processo R e usa SQL Satellite per gestire il trasferimento dei dati tra R e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

BxlServer è complementare a R, in quanto interagisce con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] per supportare l'integrazione di R con SQL Server. BXL è l'acronimo di linguaggio Exchange binario e fa riferimento al formato dei dati utilizzato per spostare i dati in modo efficiente tra SQL Server e i processi esterni, ad esempio R. BxlServer.dll viene installato anche quando si installa il Client R Microsoft o Microsoft R Server.

SQL Satellite è una nuova API di estendibilità in SQL Server 2016 fornita dal motore di database per supportare il codice esterno o i runtime esterni implementati usando C o C++. BxlServer usa SQL Satellite per comunicare con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

SQL Satellite usa un formato di dati personalizzato ottimizzato per il trasferimento rapido dei dati tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e i linguaggi di script esterni. Esegue le conversioni dei tipi e definisce gli schemi dei set di dati di input e output durante le comunicazioni tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e R.

BxlServer usa SQL Satellite per queste attività:

  + Lettura dei dati di input
  + Scrittura dei dati di output
  + Recupero degli argomenti di input
  + Scrittura degli argomenti di output
  + Gestione degli errori
  + Errori al client e output standard la scrittura

È possibile monitorare SQL Satellite usando gli eventi estesi. Per altre informazioni, vedere [Eventi estesi per SQL Server R Services](extended-events-for-sql-server-r-services.md).

## <a name="communication-channels-between-components"></a>Canali di comunicazione tra componenti

+ **TCP/IP**

    Per impostazione predefinita, le comunicazioni interne fra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e Satellite SQL utilizzare TCP/IP.

+ **Named Pipe**

    Trasferimento dei dati interna tra il BxlServer e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] tramite SQL Satellite utilizza un formato di dati compressi di proprietario per migliorare le prestazioni. I dati vengono scambiati dalla memoria R a BxlServer tramite named pipe nel formato BXL.

+ **ODBC**

    Le comunicazioni tra i client di analisi scientifica dei dati esterna e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza utilizzare ODBC. L'account che invia i processi R per [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] deve avere entrambe le autorizzazioni per connettersi all'istanza ed eseguire gli script esterni. L'account deve anche avere le autorizzazioni per accedere ai dati usati dal processo, per scrivere i dati (ad esempio in caso di salvataggio dei risultati in una tabella) oppure per creare oggetti di database (ad esempio, in caso di salvataggio delle funzioni R come parte di una nuova stored procedure).

    Quando si usa [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] come contesto di calcolo per un processo R inviato da un client remoto e il comando R deve recuperare i dati da un'origine esterna, viene usato ODBC per il writeback. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] associa l'identità dell'utente che invia il comando R remoto all'identità dell'utente dell'istanza corrente ed esegue il comando ODBC usando le credenziali di tale utente. La stringa di connessione necessaria per eseguire questa chiamata a ODBC viene ottenuta dal codice client.

    Possono essere effettuate altre chiamate ODBC nello script tramite **RODBC**. RODBC è un pacchetto R molto diffuso usato per accedere ai dati nei database relazionali. Le sue prestazioni sono tuttavia generalmente più lente di quelle di provider analoghi usati da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Molti script R usano le chiamate incorporate a RODBC come modo per recuperare set di dati "secondari" da usare nelle analisi. La stored procedure che esegue il training di un modello potrebbe ad esempio definire una query SQL per ottenere i dati per il training di un modello, ma usare una chiamata a RODBC incorporata per ottenere fattori aggiuntivi, eseguire ricerche o ottenere nuovi dati da origini esterne, come file di testo o Excel.

    Il codice seguente illustra una chiamata a RODBC incorporata in uno script R:

    ```R
    library(RODBC);
    connStr <- paste("Driver=SQL Server;Server=", instance_name, ";Database=", database_name, ";Trusted_Connection=true;", sep="");
    dbhandle <- odbcDriverConnect(connStr)
    OutputDataSet <- sqlQuery(dbhandle, "select * from table_name");
    ```

+ **Altri protocolli**

    Inoltre è possono utilizzare i processi che potrebbe essere necessario lavorare in "blocchi" o trasferire i dati a un client remoto di. Formato con estensione XDF supportato da Microsoft R. effettivo trasferimento di dati è tramite BLOB codificato.

## <a name="interaction-of-components"></a>Interazione tra componenti

L'architettura dei componenti appena descritta è stata fornita per garantire che il codice R open source possa funzionare "così com'è", offrendo prestazioni notevolmente migliorate per il codice in esecuzione in un computer [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Il meccanismo di interazione dei componenti con il runtime R e il motore di database di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] è diverso a seconda della modalità di avvio del codice R. Gli scenari principali sono riepilogati in questa sezione.

### <a name="r-scripts-executed-from-sql-server-in-database"></a>Script R eseguiti da SQL Server nel database

Il codice R eseguito dall'interno di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] viene eseguito chiamando una stored procedure. Qualsiasi applicazione in grado di eseguire una chiamata a una stored procedure può quindi avviare l'esecuzione del codice R.  Successivamente, [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] gestisce l'esecuzione del codice R, come riepilogato nel diagramma seguente.

![rsql_indb780-01](media/script_in-db-r.png)

1. Una richiesta per il runtime R è indicata dal parametro _@language='R'_ passato alla stored procedure, [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md). [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] invia la richiesta al servizio Launchpad.
2. Il servizio Launchpad avvia l'utilità di avvio appropriata, in questo caso, RLauncher.
3. RLauncher avvia il processo R esterno.
4. BxlServer si coordina con il runtime R per gestire gli scambi di dati con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e l'archiviazione dei risultati.
5. SQL Satellite gestisce le comunicazioni sulle attività correlate e i processi con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
6. BxlServer usa SQL Satellite per comunicare lo stato e i risultati a [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
7. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ottiene i risultati e chiude le attività e i processi correlati.

### <a name="r-scripts-executed-from-a-remote-client"></a>Script R eseguiti da un client remoto

Durante la connessione da un client di analisi scientifica dei dati remota che supporta Microsoft R, è possibile eseguire funzioni R nel contesto di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] utilizzando le funzioni RevoScaleR. Si tratta di un flusso di lavoro diverso dal precedente, riepilogato nel diagramma seguente.

![rsql_fromR2db-01](media/remote-sqlcc-from-r2.png)

1. Per le funzioni RevoScaleR, il runtime di R chiama una funzione di collegamento che a sua volta chiama BxlServer.
2. BxlServer viene fornito con Microsoft R ed eseguito in un processo separato dal runtime R.
3. BxlServer determina la destinazione della connessione e avvia una connessione tramite ODBC, passando le credenziali fornite come parte della stringa di connessione nell'oggetto origine dati R.
4. BxlServer apre una connessione all'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
5. Per una chiamata di R, la finestra di avvio servizio viene richiamato, che è attiva, viene avviata l'utilità di avvio appropriato, RLauncher. Da questo momento, l'elaborazione del codice R è simile al processo per l'esecuzione di codice R da T-SQL.
6. RLauncher effettua una chiamata all'istanza del runtime R installata nel computer [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
7. I risultati vengono restituiti a BxlServer.
8. SQL Satellite gestisce le comunicazioni con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e la pulizia degli oggetti processo correlati.
9. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] passa i risultati al client.

## <a name="next-steps"></a>Passaggi successivi

[Panoramica dell'architettura](architecture-overview-sql-server-r.md)

[Panoramica della sicurezza](security-overview-sql-server-r.md)

[Considerazioni sulla sicurezza](security-considerations-for-the-r-runtime-in-sql-server.md)
