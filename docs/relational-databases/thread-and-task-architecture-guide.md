---
title: "Guida sull'architettura dei thread e delle attività | Microsoft Docs"
ms.custom: 
ms.date: 10/26/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- guide, thread and task architecture
- thread and task architecture guide
ms.assetid: 925b42e0-c5ea-4829-8ece-a53c6cddad3b
caps.latest.revision: 3
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 93be3a22ee517f90e65b8c8ba6dcaa8d90ed8515
ms.openlocfilehash: 3b835536b4f510021f0d966e3214cf1ec5f71f5c
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="thread-and-task-architecture-guide"></a>guida sull'architettura dei thread e delle attività
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

I thread rappresentano una caratteristica del sistema operativo che consente di suddividere la logica dell'applicazione in più percorsi di esecuzione simultanei. Questa caratteristica è utile quando in applicazioni complesse è necessario eseguire numerose attività simultaneamente. 

Quando esegue un'istanza di un'applicazione, il sistema operativo crea un'unità denominata processo per gestire l'istanza. Il processo dispone di un thread di esecuzione. Si tratta di una serie di istruzioni di programmazione eseguite dal codice dell'applicazione. In un'applicazione semplice con un singolo set di istruzioni che è possibile eseguire in serie, ad esempio, è disponibile un singolo percorso di esecuzione, o thread, per tutta l'applicazione. Nelle applicazioni più complesse è possibile eseguire più attività in parallelo, anziché in serie, avviando processi distinti per ogni attività. L'avvio di un processo, tuttavia, rappresenta un'operazione che richiede un numero elevato di risorse. In alternativa, l'applicazione può avviare thread distinti, che richiedono una quantità minore di risorse. Ogni thread, inoltre, può essere pianificato per l'esecuzione indipendentemente dagli altri thread associati al processo.

I thread consentono alle applicazioni complesse di ottimizzare l'utilizzo della CPU anche nel caso di computer con una singola CPU che possono eseguire un solo thread per volta. Se un thread esegue un'operazione che richiede tempi prolungati e non utilizza la CPU, ad esempio un'operazione di lettura o scrittura su disco, può essere eseguito un altro thread fino al completamento della prima operazione. La possibilità di eseguire thread mentre altri thread sono in attesa del completamento di un'operazione consente all'applicazione di ottimizzare l'utilizzo della CPU. Questo vale in particolare per le applicazioni multiutente che eseguono una grande quantità di I/O su disco, ad esempio i server di database. I computer con più microprocessori o CPU possono eseguire contemporaneamente un thread per ogni CPU. Se un computer dispone di otto CPU, ad esempio, può eseguire otto thread simultaneamente.

## <a name="sql-server-batch-or-task-scheduling"></a>Pianificazione delle attività o dei batch di SQL Server

### <a name="allocating-threads-to-a-cpu"></a>Allocazione di thread a una CPU

Per impostazione predefinita, ogni istanza di SQL Server avvia ogni thread. Se è stata abilitata l'affinità, il sistema operativo assegna ogni thread a una CPU specifica. Il sistema operativo distribuisce i thread delle istanze di SQL Server tra i microprocessori, o CPU, di un computer in base al carico. In alcuni casi, è inoltre possibile che il sistema operativo trasferisca un thread da una CPU con un elevato carico di lavoro a un'altra. Di contro, il motore di database di SQL Server assegna thread di lavoro alle utilità di pianificazione che distribuiscono uniformemente i thread fra le CPU.

L'opzione della maschera di affinità viene impostata tramite [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md). Quando la maschera di affinità non è impostata, l'istanza di SQL Server alloca uniformemente il numero di thread di lavoro fra le utilità di pianificazione che non sono state escluse.

### <a name="using-the-lightweight-pooling-option"></a>Utilizzo dell'opzione lightweight pooling

Lo scambio del contesto dei thread non determina un overhead molto elevato. Per la maggior parte delle istanze di SQL Server non si verificheranno differenze di prestazione tra l'impostazione dell'opzione lightweight pooling su 0 o 1. Le uniche istanze di SQL Server che possono trarre beneficio dall'opzione [lightweight pooling](../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md) sono quelle in esecuzione in un computer con le caratteristiche seguenti:    
* Server di grandi dimensioni con più CPU.
* Le risorse di tutte le CPU sono impegnate quasi al massimo.
* Viene eseguita un'intensa attività di scambio del contesto.

Le prestazioni di questi sistemi potrebbero migliorare impostando il valore dell'opzione lightweight pooling su 1.

Si consiglia di non utilizzare la modalità fiber per la pianificazione dell'operazione di routine. Questo perché può ridurre le prestazione bloccando i vantaggi normali dello scambio del contesto e perché alcuni componenti di SQL Server non possono funzionare correttamente in modalità fiber. Per altre informazioni, vedere lightweight pooling.

## <a name="thread-and-fiber-execution"></a>Thread ed esecuzione in modalità fiber

Microsoft Windows utilizza un sistema a priorità numerica che utilizza intervalli compresi tra 1 e 31 per la pianificazione dei thread per l'esecuzione. Lo zero è riservato all'utilizzo da parte del sistema operativo. Quando più thread sono in attesa di esecuzione, Windows esegue il dispatch del thread con la priorità più alta.

Per impostazione predefinita, ogni istanza di SQL Server ha priorità 7, che è considerata la priorità normale. In questo modo ai thread di SQL Server viene assegnata una priorità sufficientemente alta per ottenere le risorse della CPU necessarie senza produrre effetti negativi sulle altre applicazioni. 

È possibile usare l'opzione di configurazione [priority boost](../database-engine/configure-windows/configure-the-priority-boost-server-configuration-option.md) per aumentare fino a 13 il livello di priorità dei thread di un'istanza di SQL Server. (alta priorità). Questa impostazione consente di assegnare ai thread di SQL Server una priorità maggiore di quella della maggior parte delle altre applicazioni. Pertanto, il dispatch dei thread di SQL Server viene eseguito non appena è possibile eseguire i thread, che non vengono quindi preceduti dai thread di altre applicazioni. Le prestazioni vengono migliorate se nel server sono in esecuzione solo istanze di SQL Server e non altre applicazioni. Tuttavia, se in SQL Server viene eseguita un'operazione che impegna notevolmente la memoria, è probabile che la priorità delle altre applicazioni non sia maggiore di quella del thread di SQL Server. 

Se vengono eseguite più istanze di SQL Server nello stesso computer e solo per alcune è impostata l'opzione priority boost, le prestazioni delle istanze in esecuzione con priorità normale potrebbero risentirne. Le prestazioni delle altre applicazioni e degli altri componenti sul server possono ridursi se priority boost è abilitato. Pertanto, è consigliabile utilizzarlo solo in condizioni assolutamente controllate.


## <a name="hot-add-cpu"></a>Aggiunta di CPU a caldo

Per aggiunta di CPU a caldo si intende la possibilità di aggiungere CPU a un sistema in esecuzione in modo dinamico. L'aggiunta di CPU può verificarsi fisicamente tramite l'aggiunta di nuovi componenti hardware, in modo logico tramite il partizionamento hardware online o virtualmente tramite un livello di virtualizzazione. A partire da SQL Server 2008, SQL Server supporta l'aggiunta a caldo di CPU.

Requisiti per l'aggiunta di CPU a caldo:  
* È necessario disporre di hardware che supporta l'aggiunta di CPU a caldo.
* È necessario disporre della versione a 64 bit di Windows Server 2008 Datacenter o del sistema operativo Windows Server 2008 Enterprise Edition per sistemi con processore Itanium.
* Richiede SQL Server Enterprise.
* Non è possibile configurare SQL Server per l'uso di Soft-NUMA. Per altre informazioni su Soft-NUMA, vedere [Soft-NUMA (SQL Server)](../database-engine/configure-windows/soft-numa-sql-server.md).

SQL Server non inizia automaticamente a usare le CPU aggiunte. In tal modo si evita che SQL Server faccia uso di CPU che potrebbero essere state aggiunte per altri scopi. Dopo aver aggiunto le CPU, eseguire l'istruzione [RECONFIGURE](../t-sql/language-elements/reconfigure-transact-sql.md) per consentire a SQL Server di riconoscere le nuove CPU come risorse disponibili.

> [!NOTE]
> Se è configurata l'opzione [affinity64 mask](../database-engine/configure-windows/affinity64-mask-server-configuration-option.md) , sarà necessario modificarla per consentire l'uso delle nuove CPU.
 

## <a name="best-practices-for-running-sql-server-on-computers-that-have-more-than-64-cpus"></a>Procedure consigliate per l'esecuzione di SQL Server in computer che dispongono di oltre 64 CPU

### <a name="assigning-hardware-threads-with-cpus"></a>Assegnazione di thread di hardware alle CPU

Non usare le opzioni di configurazione del server affinity mask e affinity64 mask per associare processori a thread specifici. Queste opzioni sono limitate a 64 CPU. Usare invece l'opzione SET PROCESS AFFINITY di [ALTER SERVER CONFIGURATION](../t-sql/statements/alter-server-configuration-transact-sql.md) .

### <a name="managing-the-transaction-log-file-size"></a>Gestione delle dimensioni del file del log delle transazioni

Non utilizzare l'aumento automatico per aumentare le dimensioni del file del log delle transazioni. L'aumento del log delle transazioni deve essere eseguito tramite un processo seriale. L'estensione del log può impedire il proseguimento delle operazioni di scrittura della transazioni fino al suo completamento. Preallocare invece lo spazio per i file di log impostando le dimensioni dei file su un valore sufficientemente elevato per supportare il tipico carico di lavoro nell'ambiente.

### <a name="setting-max-degree-of-parallelism-for-index-operations"></a>Impostazione del grado massimo di parallelismo per le operazioni sugli indici

Le prestazioni delle operazioni sugli indici, quali la creazione o la ricompilazione degli indici, possono essere ottimizzate nei computer dotati di molte CPU impostando temporaneamente il modello di recupero del database sul modello con registrazione minima delle operazioni bulk o sul modello con registrazione minima. Queste operazioni sugli indici possono generare attività del log significative e le contese relative al log possono influire sul grado di parallelismo selezionato in SQL Server.

Inoltre, provare a regolare il **massimo grado di parallelismo (MAXDOP)** opzione di configurazione del server per queste operazioni. Le linee guida seguenti sono basate su test interni e costituiscono consigli generali. È consigliabile provare diverse impostazioni MAXDOP per determinare quella ottimale per l'ambiente.

* Per il modello di recupero con registrazione completa, limitare l'opzione Massimo grado di parallelismo a un valore minore o uguale a 8.   
* Per il modello di recupero con registrazione minima delle operazioni bulk o per il modello di recupero con registrazione minima, è consigliabile impostare l'opzione Massimo grado di parallelismo su un valore maggiore di 8.   
* Nei server con configurazione NUMA, il grado massimo di parallelismo non deve superare il numero di CPU assegnate a ogni nodo NUMA. Ciò è dovuto al fatto che la query utilizzerà con maggiore probabilità memoria locale da un nodo NUMA, migliorando i tempi di accesso alla memoria.  
* Per i server con hyper-threading abilitata e prodotti nel 2009 sono versioni precedenti (prima che la funzionalità hyper-threading è stata migliorata), il valore MAXDOP non deve superare il numero di processori fisici, invece di processori logici.

Per ulteriori informazioni sull'opzione max degree of parallelism, vedere [il max degree of parallelism opzione di configurazione Server Configurare](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).

### <a name="setting-the-maximum-number-of-worker-threads"></a>Impostazione del numero massimo di thread di lavoro

Impostare sempre il numero massimo di thread di lavoro in modo che sia superiore al grado massimo di parallelismo impostato. Il numero di thread di lavoro deve essere impostato sempre su un valore almeno sette volte superiore al numero di CPU presenti nel server. Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max worker threads](../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md).

### <a name="using-sql-trace-and-sql-server-profiler"></a>Utilizzo di Traccia SQL e SQL Server Profiler

 Non è consigliabile usare Traccia SQL e SQL Server Profiler in un ambiente di produzione. L'overhead per l'esecuzione di questi strumenti, inoltre, aumenta in funzione del numero di CPU. Se è necessario utilizzare Traccia SQL in un ambiente di produzione, ridurre al minimo il numero di eventi di traccia. Profilare e testare accuratamente ogni evento di traccia soggetto a carico ed evitare di utilizzare combinazioni di eventi che influiscono notevolmente sulle prestazioni.

### <a name="setting-the-number-of-tempdb-data-files"></a>Impostazione del numero di file di dati di tempdb

In genere, il numero di file di file tempdb deve corrispondere al numero di CPU. Tuttavia, considerando attentamente le esigenze di concorrenza dei file tempdb, è possibile ridurre le funzioni di gestione del database. Ad esempio, se un sistema dispone di 64 CPU e solo 32 query utilizzano in genere file tempdb, aumentando il numero di file tempdb a 64 le prestazioni non miglioreranno.

### <a name="sql-server-components-that-can-use-more-than-64-cpus"></a>Componenti di SQL Server che possono utilizzare più di 64 CPU

Nella tabella seguente sono elencati i componenti di SQL Server e viene indicato se possano o meno usare più di 64 CPU.

|Nome del processo   |Programma eseguibile |Utilizza più di 64 CPU |  
|----------|----------|----------|  
|Motore di database di SQL Server |Sqlserver.exe  |Sì |  
|Reporting Services |Rs.exe |No |  
|Analysis Services  |As.exe |No |  
|Integration Services   |Is.exe |No |  
|Service Broker |Sb.exe |No |  
|Ricerca full-text   |Fts.exe    |No |  
|SQL Server Agent   |Sqlagent.exe   |No |  
|SQL Server Management Studio   |Ssms.exe   |No |  
|Installazione di SQL Server   |Setup.exe  |No |  



