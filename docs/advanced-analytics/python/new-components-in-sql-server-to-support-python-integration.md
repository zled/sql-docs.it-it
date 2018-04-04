---
title: I componenti per l'integrazione di Python con SQL Server | Documenti Microsoft
ms.custom: ''
ms.date: 11/03/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: a35b592ef3d6d89bb3014962b9fca80816240315
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="components-in-sql-server-to-support-python-integration"></a>Componenti di SQL Server per supportare l'integrazione di Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

A partire da SQL Server 2017, servizi di Machine Learning supporta Python come un linguaggio esterno che può essere eseguito da T-SQL o eseguita in modalità remota tramite SQL Server come contesto di calcolo.

In questo argomento vengono descritti i componenti in SQL Server 2017 che supportano l'estensibilità in generale e nel linguaggio Python in modo specifico.

## <a name="sql-server-components-and-providers"></a>I provider e i componenti di SQL Server

Per configurare SQL Server 2017 per consentire l'esecuzione di script Python è un processo costituito da più passaggi.

1. Installare la funzionalità di estendibilità.
2. Abilitare la funzionalità di esecuzione dello script esterno.
3. Riavviare il servizio motore di database.

Potrebbero essere necessari passaggi aggiuntivi per supportare l'esecuzione degli script remoti.

Per altre informazioni, vedere [installare SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md).

### <a name="launchpad"></a>Launchpad

Il Launchpad attendibile di SQL Server è un servizio introdotto in SQL Server 2016 che gestisce ed esegue gli script esterni, simili a quello in cui il servizio di indicizzazione e query full-text avvia un host separato per l'elaborazione delle query full-text.

Il servizio Launchpad possa avviare solo attendibile avvio che vengono pubblicati da Microsoft o che sono certificate da Microsoft come soddisfano i requisiti per la gestione delle prestazioni e risorsa.

+ SQL Server 2017 supporta R e 3.5 di Python
+ SQL Server 2016 supporta R

Il servizio [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] viene eseguito con il relativo account utente.

> [!TIP]
> Se si modifica l'account che esegue Launchpad, prestare attenzione a tale scopo utilizzando Gestione configurazione SQL Server, per garantire che le modifiche vengono scritte per i file correlati.

Per eseguire le attività in una lingua supportata specifica, la finestra di avvio Ottiene un account di lavoro protetti dal pool e avvia un processo satellite per gestire il runtime esterno:

+ Rlauncher. dll per il linguaggio R
+ Pythonlauncher.dll per Python 3.5

Ogni processo satellite eredita l'account utente della finestra di avvio e Usa l'account di lavoro per la durata dell'esecuzione dello script. Se lo script Python utilizza processi paralleli, vengono creati con l'account di lavoro stessa.

Per ulteriori informazioni sul contesto di sicurezza della finestra di avvio, vedere [sicurezza](security-overview-sql-server-python-services.md).

### <a name="bxlserver-and-sql-satellite"></a>BxlServer e Satellite SQL

Se si esegue [Process Explorer](https://technet.microsoft.com/sysinternals/processexplorer.aspx) mentre è in esecuzione un processo di Python, si noterà una o più istanze di BxlServer.

**BxlServer** è un eseguibile fornito da Microsoft che gestisce la comunicazione tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e Python (o R). Crea gli oggetti di processo di Windows che vengono utilizzati per contenere le sessioni dello script esterno, esegue il provisioning sicuro le cartelle di lavoro per ogni processo di script esterni e utilizza SQL Satellite per gestire il trasferimento di dati tra il runtime esterno e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

In effetti, BxlServer è abbinato al Python che funziona con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] per trasferire i dati e le attività di gestione. BXL è l'acronimo di linguaggio Exchange binario e fa riferimento al formato di dati utilizzato per spostare in modo efficiente i dati tra SQL Server e i processi esterni. BxlServer è anche una parte importante di Microsoft R Client e Microsoft R Server.

**SQL Satellite** è un'API di estensibilità, inclusi nel motore di database a partire da SQL Server 2016, che supporta codice esterno o Runtime esterni implementati utilizzando C o C++.

BxlServer usa SQL Satellite per queste attività:

+ Lettura dei dati di input
+ Scrittura dei dati di output
+ Recupero degli argomenti di input
+ Scrittura degli argomenti di output
+ Gestione degli errori
+ Scrittura di STDOUT e STDERR nel client

Satellite SQL viene utilizzato un formato di dati personalizzati che è ottimizzato per il trasferimento di dati rapido tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e linguaggi di script esterni. Esegue le conversioni di tipo e definisce gli schemi dei set di dati di input e output durante le comunicazioni tra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e di runtime dello script esterno.

Satellite SQL può essere monitorato mediante windows (XEvent) eventi estesi. Per altre informazioni, vedere [degli eventi estesi per R](../../advanced-analytics/r/extended-events-for-sql-server-r-services.md).

## <a name="communication-channels-between-components"></a>Canali di comunicazione tra componenti

+ **TCP/IP**

  Per impostazione predefinita, le comunicazioni interne fra [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e Satellite SQL utilizzare TCP/IP.

+ **Named Pipe**

  Il trasporto dei dati interni tra BxlServer e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] tramite SQL Satellite usa un formato di dati compresso proprietario per migliorare le prestazioni. Scambio di dati Python e BxlServer in formato BXL, tramite Named pipe.

+ **ODBC**

  Le comunicazioni tra i client di analisi scientifica dei dati esterna e [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] istanza utilizzare ODBC. L'account che invia lo script dei processi per [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] deve avere entrambe le autorizzazioni per connettersi all'istanza e per eseguire gli script esterni.

  Inoltre, a seconda dell'attività, l'account potrebbe essere necessario queste autorizzazioni:

  + Leggere i dati utilizzati dal processo
  + Scrivere dati in tabelle: ad esempio, quando il salvataggio comporta a una tabella
  + Creare oggetti di database: ad esempio, se il salvataggio dello script esterno come parte di una nuova stored procedure.

  Quando [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] viene usato come contesto di calcolo per Python script eseguito da un client remoto e il file eseguibile Python deve recuperare dati da un'origine esterna, ODBC viene utilizzato per il writeback. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Associa l'identità dell'utente che invia il comando remoto all'identità dell'utente nell'istanza corrente e viene eseguito il comando ODBC utilizzando le credenziali dell'utente. La stringa di connessione necessaria per eseguire questa chiamata a ODBC viene ottenuta dal codice client.

## <a name="interaction-of-components"></a>Interazione dei componenti

I diagrammi seguenti illustrano l'interazione dei componenti di SQL Server con il runtime di Python in ognuno degli scenari supportati: esecuzione di script nel database e remoti da un terminale di Python, utilizzando un contesto di calcolo di SQL Server.

### <a name="python-scripts-executed-in-database"></a>Script Python eseguita nel database

Quando si esegue Python "interni" [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è necessario incapsulare dello script Python all'interno di una stored procedure speciale [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Dopo che lo script è stato incorporato nella stored procedure, tutte le applicazioni che garantiscono una stored procedure chiamata possono avviare l'esecuzione del codice Python.  Successivamente [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] gestisce l'esecuzione di codice, come riepilogato nel diagramma seguente.

![script-in-db-python](../../advanced-analytics/python/media/script-in-db-python2.png)

1. Una richiesta per il runtime di Python è indicata dal parametro `@language='Python'` passato alla stored procedure. SQL Server invia la richiesta per il servizio Launchpad.
2. Il servizio Launchpad avvia l'utilità di avvio appropriata; In questo caso, PythonLauncher.
3. PythonLauncher avvia il processo Python35 esterno.
4. BxlServer interagisce con il runtime di Python per gestire gli scambi di dati e archiviazione dei risultati di lavoro.
5. SQL Satellite che gestisce le comunicazioni sulle attività correlate ed elabora con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
6. BxlServer usa SQL Satellite per comunicare lo stato e i risultati a [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
7. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ottiene i risultati e chiude le attività e i processi correlati.

### <a name="python-scripts-executed-from-a-remote-client"></a>Script Python eseguiti da un client remoto

È possibile eseguire script Python da un computer remoto, ad esempio un computer portatile e li vengono eseguite nel contesto del computer SQl Server, se vengono soddisfatte queste condizioni:

+ Progettare in modo appropriato gli script
+ Il computer remoto è installato le librerie di estendibilità che vengono utilizzate dai servizi di Machine Learning. Il [revoscalepy](what-is-revoscalepy.md) pacchetto è necessario usare contesti di calcolo remoti.

Nel diagramma seguente viene riepilogato il flusso di lavoro globale quando gli script vengono inviati da un computer remoto.

![remote-sqlcc-from-python](../../advanced-analytics/python/media/remote-sqlcc-from-python3.png)

1. Per le funzioni che sono supportate in **revoscalepy**, il runtime di Python chiama una funzione di collegamento, che a sua volta chiama BxlServer.
2. BxlServer è incluso in Machine Learning Services (In-Database) e viene eseguito in un processo separato dal runtime di Python.
3. BxlServer determina la destinazione della connessione e avvia una connessione tramite ODBC, passando le credenziali fornite come parte della stringa di connessione nello script Python.
4. BxlServer apre una connessione all'istanza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
5. Quando viene chiamato un tempo di esecuzione dello script esterno, il servizio Launchpad viene richiamato, che a sua volta avvia l'utilità di avvio appropriato: in questo caso, PythonLauncher.dll. Successivamente, l'elaborazione del codice Python viene gestita in un flusso di lavoro simile a quella quando viene richiamato codice Python da una stored procedure in T-SQL.
6. PythonLauncher effettua una chiamata all'istanza di Python cui è installato il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer.
7. I risultati vengono restituiti a BxlServer.
8. SQL Satellite gestisce le comunicazioni con [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e la pulizia degli oggetti processo correlati.
9. [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] passa i risultati al client.

## <a name="next-steps"></a>Passaggi successivi

[Panoramica dell'architettura per Python in SQL Server](architecture-overview-sql-server-python.md)
