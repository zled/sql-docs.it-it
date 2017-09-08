---
title: I componenti per l'integrazione di Python con SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 08/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 07f8e18b4481b2773f3ac16cdea08c27feff1ba3
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="components-in-sql-server-to-support-python-integration"></a>Componenti di SQL Server per supportare l'integrazione di Python

A partire da SQL Server 2017, servizi di Machine Learning supporta Python come un linguaggio esterno che può essere eseguito da T-SQL o eseguita in modalità remota tramite SQL Server come contesto di calcolo.

Questo argomento descrive in modo specifico i componenti di SQL Server 2017 che supportano l'estensibilità in generale e la lingua di Python.

## <a name="sql-server-components-and-providers"></a>Provider e i componenti di SQL Server

Per configurare SQL Server 2017 per consentire l'esecuzione di script Python è un processo costituito da più passaggi.

1. Installare la funzionalità di estendibilità.
2. Abilitare la funzionalità di esecuzione dello script esterno.
3. Riavviare il servizio motore di database.

Potrebbero essere necessari passaggi aggiuntivi per supportare l'esecuzione degli script remoti.

Per ulteriori informazioni, vedere [configurare servizi di Machine Learning](setup-python-machine-learning-services.md)

### <a name="launchpad"></a>Launchpad

Il Launchpad attendibile di SQL Server è un servizio introdotto in SQL Server 2016 che gestisce ed esegue gli script esterni, allo stesso modo in cui il servizio di indicizzazione e query full-text avvia un host separato per l'elaborazione delle query full-text.

Il servizio Launchpad possa avviare solo attendibile avvio che vengono pubblicati da Microsoft o che sono certificate da Microsoft come soddisfano i requisiti per la gestione delle prestazioni delle risorse.

+ SQL Server 2017 supporta R e 3.5 di Python
+ SQL Server 2016 supporta R

Il servizio [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] viene eseguito con il relativo account utente.

> [!TIP]
> Se si modifica l'account che esegue una finestra di avvio, assicurarsi di farlo mediante Gestione configurazione SQL Server, per garantire che le modifiche vengono scritte per i file correlati.

Per eseguire attività in una lingua supportata specifica, la finestra di avvio Ottiene un account di lavoro protetti dal pool e avvia un processo satellite per gestire il runtime esterno:

+ RLauncher.dll per il linguaggio R
+ Pythonlauncher.dll per Python 3.5

Ogni processo satellite eredita l'account utente della finestra di avvio e Usa l'account di lavoro per la durata dell'esecuzione dello script. Se lo script Python utilizza processi paralleli, vengono creati con l'account di lavoro stessa.

Per ulteriori informazioni sul contesto di sicurezza della finestra di avvio, vedere [sicurezza](security-overview-sql-server-python-services.md).

### <a name="bxlserver-and-sql-satellite"></a>BxlServer e Satellite SQL

Se si esegue [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) mentre è in esecuzione un processo di Python, si potrebbero vedere una o più istanze di BxlServer.

**BxlServer** è un eseguibile fornito da Microsoft che gestisce la comunicazione tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e Python (o R). Crea gli oggetti di processo di Windows che vengono utilizzati per contenere le sessioni di script esterni, disposizioni sicuro le cartelle di lavoro per ogni processo di script esterni e utilizza SQL Satellite per gestire il trasferimento di dati tra il runtime esterno e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

In effetti, BxlServer è abbinato al Python che funziona con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] per trasferire i dati e le attività di gestione. BXL è l'acronimo di linguaggio Exchange binario e fa riferimento al formato dei dati utilizzato per spostare in modo efficiente i dati tra SQL Server e i processi esterni. BxlServer è anche una parte importante di Microsoft R Client e Microsoft R Server.

**SQL Satellite** è un'API di estensibilità, inclusi nel motore di database a partire da SQL Server 2016, che supporta codice esterno o Runtime esterni implementati utilizzando C o C++.

BxlServer usa SQL Satellite per queste attività:

+ Lettura dei dati di input
+ Scrittura dei dati di output
+ Recupero degli argomenti di input
+ Scrittura degli argomenti di output
+ Gestione degli errori
+ Scrittura di STDOUT e STDERR nel client

Satellite SQL viene utilizzato un formato di dati personalizzato che è ottimizzato per il trasferimento di dati rapido tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e linguaggi di script esterni. Esegue le conversioni di tipo e definisce gli schemi dei set di dati di input e output durante le comunicazioni tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e di runtime dello script esterno.

Satellite SQL può essere monitorato mediante estesi (XEvent) eventi di windows. Per ulteriori informazioni, vedere [degli eventi estesi per R](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md).

## <a name="communication-channels-between-components"></a>Canali di comunicazione tra componenti

+ **TCP/IP**

  Per impostazione predefinita, le comunicazioni interne fra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e Satellite SQL utilizzare TCP/IP.

+ **Named Pipe**

  Il trasporto dei dati interni tra BxlServer e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] tramite SQL Satellite usa un formato di dati compresso proprietario per migliorare le prestazioni. Scambio di dati Python e BxlServer in formato BXL, tramite Named pipe.

+ **ODBC**

  Le comunicazioni tra i client di analisi scientifica dei dati esterna e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza utilizzare ODBC. L'account che invia lo script dei processi per [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] deve avere entrambe le autorizzazioni per connettersi all'istanza e per eseguire gli script esterni.

  Inoltre, a seconda dell'attività, l'account potrebbe essere necessario queste autorizzazioni:

  + Leggere i dati utilizzati dal processo
  + Scrivere dati in tabelle: ad esempio, quando il salvataggio risultati in una tabella
  + Creare oggetti di database: ad esempio, se il salvataggio dello script esterno come parte di una nuova stored procedure.

  Quando [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] viene usato come contesto di calcolo per Python script eseguito da un client remoto e il file eseguibile Python deve recuperare dati da un'origine esterna, ODBC viene utilizzato per il writeback. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]verrà mappare l'identità dell'utente che invia il comando remoto per l'identità dell'utente nell'istanza corrente, quindi eseguire il comando ODBC utilizzando le credenziali dell'utente. La stringa di connessione necessaria per eseguire questa chiamata a ODBC viene ottenuta dal codice client.

## <a name="interaction-of-components"></a>Interazione tra componenti

I diagrammi seguenti illustrano l'interazione dei componenti di SQL Server con il runtime di Python in ognuno degli scenari supportati: esecuzione di script nel database e remoti da un terminale di Python, utilizzando un contesto di calcolo di SQL Server.

### <a name="python-scripts-executed-in-database"></a>Script Python eseguita nel database

Quando si esegue Python "interni" [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è necessario incapsulare Python script all'interno di una stored procedure speciale [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Dopo lo script è stato incorporato in stored procedure, qualsiasi applicazione che è possibile effettuare una stored procedure chiamata può avviare l'esecuzione del codice Python.  Successivamente [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] gestisce l'esecuzione del codice, come riepilogato nel diagramma seguente.

![script in db python.](../../advanced-analytics/python/media/script-in-db-python.png)

1. Una richiesta per il runtime di Python è indicata dal parametro  _@language= 'Python'_ passato alla stored procedure. SQL Server invia la richiesta per il servizio Launchpad.
2. Il servizio Launchpad avvia l'utilità di avvio appropriata; In questo caso, PythonLauncher.
3. PythonLauncher avvia il processo di Python35 esterno.
4. BxlServer interagisce con il runtime di Python per gestire gli scambi di dati e archiviazione dei risultati di lavoro.
5. SQL Satellite gestisce le comunicazioni sulle attività correlate e i processi con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
6. BxlServer usa SQL Satellite per comunicare lo stato e i risultati a [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
7. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ottiene i risultati e chiude le attività e i processi correlati.

### <a name="python-scripts-executed-from-a-remote-client"></a>Script Python eseguiti da un client remoto

È possibile eseguire script Python da un computer remoto, ad esempio un computer portatile e sono eseguite nel contesto del computer SQl Server, se vengono soddisfatte queste condizioni:

+ Progettare in modo appropriato gli script
+ Nel computer remoto sia installato le librerie di estendibilità che vengono utilizzate dai servizi di Machine Learning

Nel diagramma seguente viene riepilogato il flusso di lavoro globale quando gli script vengono inviati da un computer remoto.

![remoto sqlcc da python](../../advanced-analytics/python/media/remote-sqlcc-from-python2.png)

1. Per le funzioni che sono supportate in **revoscalepy**, il runtime di Python chiama una funzione di collegamento, che a sua volta chiama BxlServer.
2. BxlServer è incluso in servizi di Machine Learning (In-Database) e viene eseguito in un processo separato dal runtime di Python.
3. BxlServer determina la destinazione della connessione e avvia una connessione tramite ODBC, passando le credenziali fornite come parte della stringa di connessione nello script Python.
4. BxlServer apre una connessione all'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
5. Quando viene chiamato un tempo di esecuzione dello script esterno, il servizio Launchpad viene richiamato, che a sua volta avvia l'utilità di avvio appropriato: in questo caso, PythonLauncher.dll. Successivamente, l'elaborazione del codice Python viene gestita in un flusso di lavoro simile a quella quando viene richiamato il codice Python da una stored procedure in T-SQL.
6. PythonLauncher effettua una chiamata all'istanza di Python cui è installata il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer.
7. I risultati vengono restituiti a BxlServer.
8. SQL Satellite gestisce le comunicazioni con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e la pulizia degli oggetti processo correlati.
9. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] passa i risultati al client.

## <a name="next-steps"></a>Passaggi successivi

[Panoramica dell'architettura per Python in SQL Server](architecture-overview-sql-server-python.md)
