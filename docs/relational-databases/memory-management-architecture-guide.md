---
title: Guida sull'architettura di gestione della memoria | Microsoft Docs
ms.custom: 
ms.date: 10/21/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- guide, memory management architecture
- memory management architecture guide
ms.assetid: 7b0d0988-a3d8-4c25-a276-c1bdba80d6d5
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d00e5c97e6c27f3fe40b2066b5e194b8011f6b1e
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="memory-management-architecture-guide"></a>guida sull'architettura di gestione della memoria
[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]

## <a name="memory-architecture"></a>Architettura della memoria

In[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] la memoria viene acquisita e liberata in modo dinamico in base alle esigenze. In genere non è necessario che un amministratore specifichi la quantità di memoria da allocare a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. L'opzione corrispondente, tuttavia, è ancora disponibile e in alcuni ambienti è necessario impostarla.

Uno dei principali obiettivi di progettazione di tutti i software di database è la riduzione del disco I/O dal momento che le letture e le scritture del disco sono le operazioni che consumano più risorse. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] crea un pool di buffer in memoria per contenere le pagine lette dal database. Gran parte del codice in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è dedicata alla riduzione del numero di letture e scritture fisiche tra il disco e il pool di buffer. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tenta di raggiungere un equilibrio tra i due obiettivi:

* Evitare che le dimensioni del pool di buffer aumentino fino a limitare la memoria dell'intero sistema.
* Ridurre al minimo l'I/O fisico sui file di database aumentando la dimensione del pool di buffer fino a raggiungere il valore massimo possibile.


> [!NOTE]
> In un sistema con carichi pesanti, alcune query di grandi dimensioni la cui esecuzione richiede una grande quantità di memoria non possono ottenere la quantità minima di memoria richiesta e ricevono un errore di timeout mentre sono in attesa delle risorse della memoria. Per risolvere il problema, aumentare il valore dell' [opzione query wait](../database-engine/configure-windows/configure-the-query-wait-server-configuration-option.md). Per una query parallela, provare a ridurre l' [opzione Massimo grado di parallelismo](../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md).
 
> [!NOTE]
> In un sistema con carichi elevati e con un numero eccessivo di richieste di memoria, le query con merge join, sort e bitmap nel piano di query possono eliminare il bitmap quando non ottengono la memoria minima necessaria per il bitmap. Ciò può influire sulle prestazioni delle query e, se il processo di ordinamento non può essere contenuto nella memoria, è possibile aumentare l'uso delle tabelle di lavoro nel database tempdb, causando la crescita di tempdb. Per risolvere questo problema, aggiungere memoria fisica o ottimizzare le query per l'uso di un piano di query diverso e più rapido.
 
### <a name="providing-the-maximum-amount-of-memory-to-includessnoversionincludesssnoversion-mdmd"></a>Assegnazione della quantità massima di memoria a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]

Usando AWE e il privilegio Blocco di pagine in memoria, è possibile fornire al motore di database di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] le quantità di memoria seguenti. La tabella seguente include una colonna per le versioni a 32 bit non più disponibili.

| |32 bit <sup>1</sup> |64 bit
|-------|-------|-------| 
|Memoria convenzionale |Tutte le edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Fino al limite dello spazio degli indirizzi virtuali di processo: <br>- 2 GB<br>- 3 GB con parametro di avvio /3gb <sup>2</sup> <br>- 4 GB su WOW64 <sup>3</sup> |Tutte le edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Fino al limite dello spazio degli indirizzi virtuali di processo: <br>- 7 TB con architettura IA64 (IA64 non è supportato in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] e versioni successive)<br>- Valore massimo del sistema operativo con architettura x64 <sup>4</sup>
|Meccanismo AWE (consente a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di superare il limite dello spazio degli indirizzi virtuali di processo nelle piattaforme a 32 bit) |[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] edizioni Standard, Enterprise e Developer: il pool di buffer è in grado di accedere a una memoria limite di 64 GB.|Non applicabile <sup>5</sup> |
|Privilegio Blocco di pagine in memoria del sistema operativo (consente di bloccare la memoria fisica, impedendo il paging della memoria bloccata da parte del sistema operativo). <sup>6</sup> |[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] edizioni Standard, Enterprise e Developer: necessari per il processo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] che usa il meccanismo AWE. La memoria allocata tramite il meccanismo AWE non può essere trasferita. <br> La concessione di questo privilegio senza l'attivazione di AWE non ha alcun effetto sul server. |[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] edizioni Enterprise e Developer: consigliato, per evitare il paging del sistema operativo. Potrebbe determinare un miglioramento delle prestazioni a seconda del carico di lavoro. La quantità di memoria accessibile è simile a quella della memoria convenzionale. |

<sup>1</sup> Le versioni a 32 bit non sono disponibili a partire da [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
<sup>2</sup> /3gb è un parametro di avvio del sistema operativo. Per altre informazioni, consultare MSDN Library.  
<sup>3</sup> WOW64 (Windows on Windows 64) è una modalità che consente di eseguire la versione a 32 bit di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] in un sistema operativo a 64 bit.  
<sup>4</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard Edition supports up to 128 GB. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition supporta il valore massimo del sistema operativo.  
<sup>5</sup> Si noti che l'opzione sp_configure awe enabled è presente in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]a 64 bit, ma viene ignorata.    
<sup>6</sup> Se viene concesso il privilegio Blocco di pagine in memoria (LPIM), sia su supporto a 32 bit per AWE che a 64 bit indipendente, è consigliabile impostare anche la memoria massima del server.

> [!NOTE]
> Le versioni precedenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] potrebbero essere eseguite in un sistema operativo a 32 bit. L'accesso a più di 4 GB di memoria in un sistema operativo a 32 bit richiede estensioni AWE (Address Windowing Extensions) per la gestione della memoria. Queste estensioni non sono necessarie quando [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è in esecuzione su sistemi operativi a 64 bit. Per altre informazioni su AWE, vedere [Spazio degli indirizzi di processo](https://msdn.microsoft.com/library/ms189334) e [Gestione della memoria per database di grandi dimensioni](https://msdn.microsoft.com/library/ms191481) nella documentazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2008.   


## <a name="dynamic-memory-management"></a>Gestione della memoria dinamica

Il comportamento predefinito per la gestione della memoria del motore di database di Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] consiste nell'acquisire la quantità di memoria necessaria senza causare insufficienza di memoria nel sistema. Nel motore di database questo comportamento è reso possibile tramite l'uso delle API di notifica della memoria di Microsoft Windows.

Lo spazio degli indirizzi virtuali di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] può essere suddiviso in due aree distinte: lo spazio occupato dal pool di buffer e il resto. Se il meccanismo AWE è abilitato, il pool di buffer può risiedere nella memoria mappata AWE, offrendo spazio aggiuntivo per le pagine del database. 

Il pool di buffer funge da fonte primaria di allocazione della memoria di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. I componenti esterni che risiedono all'interno di un processo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , ad esempio oggetti COM, che non sono consapevoli delle funzionalità di gestione della memoria di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , usano la memoria esterna allo spazio degli indirizzi virtuali occupato dal pool di buffer.

All'avvio di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , viene calcolata la dimensione dello spazio degli indirizzi virtuali per il pool di buffer in base a parametri come la quantità di memoria fisica nel sistema, il numero di thread del server e vari parametri di avvio. In[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene riservata la quantità calcolata di spazio degli indirizzi virtuali del processo per il pool di buffer, ma viene acquisita solo la quantità di memoria fisica necessaria (ovvero ne viene eseguito il commit) per il carico corrente.

L'istanza continua quindi ad acquisire la memoria necessaria per supportare il carico di lavoro. Man mano che altri utenti si connettono ed eseguono query, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene acquisita ulteriore memoria fisica su richiesta. La memoria fisica continua a essere acquisita da un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fino a quando viene raggiunto il limite di allocazione definito dall'opzione Memoria massima del server o fino a quando in Windows viene indicato che non è più disponibile memoria in eccesso. La memoria viene liberata quando viene superato il valore dell'impostazione Memoria minima del server e in Windows viene indicata un'insufficienza di memoria disponibile.

L'avvio di altre applicazioni in un computer in cui viene eseguita un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]comporta l'utilizzo di ulteriore memoria e la quantità di memoria fisica disponibile scende al di sotto del valore di destinazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Nell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] l'utilizzo della memoria viene regolato automaticamente. Se un'altra applicazione viene arrestata e viene resa disponibile altra memoria, l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] aumenta le dimensioni della propria allocazione di memoria. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] può liberare e acquisire diversi megabyte di memoria al secondo, in modo che possa adattarsi rapidamente alle modifiche dell'allocazione della memoria.


## <a name="effects-of-min-and-max-server-memory"></a>Effetti delle opzioni min server memory e max server memory

Le opzioni di configurazione Memoria minima del server e Memoria massima del server stabiliscono il limite massimo e minimo della quantità di memoria usata dal pool di buffer del motore di database di Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Il pool di buffer non acquisisce immediatamente la quantità di memoria specificata in Memoria minima del server. ma solo la memoria necessaria per l'inizializzazione. Con l'aumentare del carico di lavoro da gestire, il motore di database continua ad acquisire la memoria necessaria per supportare il carico di lavoro. Il pool di buffer non libera la memoria acquisita fino a quando non viene raggiunta la quantità specificata in Memoria minima del server. Quando viene raggiunto il limite impostato in Memoria minima del server, il pool di buffer usa quindi l'algoritmo standard per acquisire e liberare memoria nella misura necessaria. L'unica differenza è rappresentata dal fatto che nel pool di buffer la quantità di memoria allocata non scende mai al di sotto del livello specificato in Memoria minima del server, né viene mai acquisita una quantità di memoria superiore al livello specificato Memoria massima del server.

> [!NOTE]
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] come processo acquisisce più memoria rispetto a quella specificata dall'opzione Memoria massima del server. I componenti interni ed esterni possono allocare memoria al di fuori del pool di buffer, richiedendo ulteriore memoria, ma la memoria allocata al pool di buffer in genere rappresenta la parte di memoria maggiore utilizzata da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].


La quantità di memoria acquisita dal motore di database dipende interamente dal carico di lavoro assegnato all'istanza. È possibile che per un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] che elabora un numero ridotto di richieste, la quantità di memoria allocata rimanga sempre inferiore al valore di min server memory.

Se si specifica lo stesso valore per Memoria minima del server e Memoria massima del server, quando la memoria allocata al Motore di database raggiunge tale valore, il motore di database smette di liberare e acquisire dinamicamente memoria per il pool di buffer.

Se un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è in esecuzione in un computer in cui viene spesso avviata o arrestata l'esecuzione di altre applicazioni, è possibile che l'allocazione e la deallocazione della memoria da parte dell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] rallenti l'avvio delle altre applicazioni. Se [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è solo una delle numerose applicazioni server in esecuzione in un singolo computer, può inoltre essere necessario che l'amministratore di sistema controlli la quantità di memoria allocata a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. In questi casi, è possibile usare le opzioni Memoria minima del server e Memoria massima del server per controllare la quantità di memoria che può essere impiegata da [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Per altre informazioni, vedere [Opzioni di configurazione del server Server Memory](../database-engine/configure-windows/server-memory-server-configuration-options.md).

I valori delle opzioni Memoria minima del server e Memoria massima del server vengono specificati in megabyte.

## <a name="memory-used-by-includessnoversionincludesssnoversion-mdmd-objects-specifications"></a>Memoria usata dalle specifiche degli oggetti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]

Nella seguente tabella sono indicate le quantità di memoria approssimative usate da diversi oggetti in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. I valori riportati sono stimati e possono variare a seconda dell'ambiente e dalle modalità di creazione degli oggetti.

* Blocco: 64 byte + 32 byte per proprietario   
* Connessione utente: circa (3* *network_packet_size + 94 kb)    

Le dimensioni del pacchetto di rete indicano la dimensione dei pacchetti TDS (Tabular Data Scheme) usati per le comunicazioni tra le applicazioni e il motore di database di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . La dimensione predefinita del pacchetto è 4 KB e viene controllata dall'opzione di configurazione delle dimensioni del pacchetto di rete.

Quando è abilitato MARS (Multiple Active Result Set), la connessione utente corrisponde a circa (3 + 3 * num_logical_connections) * network_packet_size + 94 KB.

## <a name="buffer-management"></a>Gestione del buffer

Lo scopo principale di un database di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è l'archiviazione e il recupero dei dati. L'esecuzione di una quantità elevata di operazioni di I/O su disco è pertanto una caratteristica fondamentale del motore di database. Poiché le operazioni di I/O nel disco possono utilizzare molte risorse e richiedere un tempo relativamente lungo per il completamento, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene data grande importanza all'efficienza dell'I/O. La gestione del buffer è un elemento chiave per il raggiungimento di tale efficienza. Il componente di gestione del buffer è costituito da due meccanismi, ovvero Gestione buffer che consente di accedere alle pagine del database e aggiornarle, e la cache del buffer, detta anche pool di buffer, che consente di ridurre le operazioni di I/O del file di database. 

### <a name="how-buffer-management-works"></a>Funzionamento della gestione del buffer

Un buffer è una pagina da 8 KB in memoria, ovvero delle stesse dimensioni di una pagina di dati o di indice. La cache del buffer è quindi suddivisa in pagine da 8 KB. Gestione buffer consente di gestire le funzioni per la lettura delle pagine di dati o di indice dai file su disco del database nella cache buffer e la riscrittura sul disco delle pagine modificate. Una pagina rimane nella cache del buffer fino a quando per Gestione buffer non è necessaria l'area del buffer per leggere un maggior numero di dati. I dati vengono riscritti sul disco solo se vengono modificati. I dati nella cache del buffer possono essere modificati più volte prima di venire riscritti sul disco. Per altre informazioni, vedere [Lettura di pagine](../relational-databases/reading-pages.md) e [Scrittura di pagine](../relational-databases/writing-pages.md).

All'avvio di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , viene calcolata la dimensione dello spazio degli indirizzi virtuali per la cache del buffer in base a parametri come la quantità di memoria fisica nel sistema, il numero massimo di thread del server configurati e vari parametri di avvio. In[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene riservata la quantità calcolata di spazio degli indirizzi virtuali del processo per la cache del buffer (chiamata destinazione di memoria), ma viene acquisita solo la quantità di memoria fisica necessaria (ovvero ne viene eseguito il commit) per il carico corrente. È possibile eseguire query sulle colonne **bpool_commit_target** e **bpool_committed columns** nella vista del catalogo [sys.dm_os_sys_info](../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md) per restituire il numero di pagine riservate come destinazione di memoria e il numero di pagine su cui attualmente viene eseguito il commit nella cache del buffer, rispettivamente.

L'intervallo tra l'avvio di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e il momento in cui alla cache del buffer viene allocata la memoria massima è detto processo di avvio. Durante questo intervallo le richieste di lettura riempiono i buffer in base alle esigenze. Ad esempio, una richiesta di lettura di pagina singola riempie una singola pagina del buffer. Questo significa che il processo di avvio dipende dal numero e dal tipo di richieste del client. Il processo di avvio viene reso più rapido mediante la trasformazione delle richieste di lettura di pagina singola in richieste di otto pagine allineate. Ciò consente un completamento del processo di avvio molto più rapido, in particolare nei computer con molta memoria.

Gestione buffer utilizza la maggior parte della memoria nel processo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e coopera pertanto con Gestione memoria per consentire agli altri componenti di utilizzare i relativi buffer. Gestione buffer interagisce essenzialmente con i componenti seguenti:

* Strumento di gestione delle risorse, per controllare l'utilizzo globale della memoria e, nelle piattaforme a 32 bit, l'utilizzo dello spazio degli indirizzi.  
* Gestione database e il sistema operativo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (SQLOS) per operazioni di I/O di file di basso livello.  
* Strumento di gestione dei log per la registrazione write-ahead.  

### <a name="supported-features"></a>Funzionalità supportate

Gestione buffer supporta le caratteristiche seguenti:

* Gestione buffer supporta NUMA (Non-Uniform Memory Access). Le pagine della cache buffer vengono distribuite tra i nodi hardware NUMA, consentendo a un thread di accedere a una pagina del buffer allocata nel nodo NUMA locale anziché dalla memoria esterna. 
* Gestione buffer supporta l'aggiunta di memoria a caldo, consentendo agli utenti di aggiungere memoria fisica senza riavviare il server. 
* Gestione buffer supporta pagine di grandi dimensioni su piattaforme a 64 bit. Le dimensioni delle pagine sono specifiche della versione di Windows utilizzata. 
* In Gestione buffer sono disponibili strumenti di diagnostica aggiuntivi esposti tramite DMV. È possibile utilizzare queste viste per monitorare varie risorse del sistema operativo specifiche di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Ad esempio, è possibile usare la vista sys.dm_os_buffer_descriptors per monitorare le pagine nella cache buffer.   

### <a name="disk-io"></a>I/O su disco
Gestione buffer esegue solo letture e scritture sul database. Altre operazioni su file e database, ad esempio apertura, chiusura, estensione e compattazione vengono eseguite dai componenti del gestore database e di File Manager. 

Le operazioni di I/O su disco eseguite da Gestione buffer hanno le caratteristiche seguenti:

* Tutti gli I/O vengono eseguiti in modo asincrono. In questo modo, il thread che esegue la chiamata può continuare l'elaborazione mentre l'operazione di I/O viene eseguita in background.
* Tutti gli I/O vengono eseguiti nei thread che eseguono la chiamata a meno che non sia in uso l'opzione affinity I/O. L'opzione affinity I/O mask associa l'I/O su disco di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a un subset di CPU specificato. Negli ambienti [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] di fascia alta con elaborazione delle transazioni online (OLTP), questa estensione può migliorare le prestazioni dei thread di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] che generano operazioni di I/O.
* Gli I/O di più pagine vengono eseguiti con un I/O non sequenziale, che consente il trasferimento di dati da e verso aree di memoria non contigue. Questo significa che [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] può riempire o scaricare rapidamente la cache buffer evitando più richieste di I/O fisici. 

#### <a name="long-io-requests"></a>Richieste di I/O lunghi  
Gestione buffer segnala qualsiasi richiesta di I/O che rimane in attesa per almeno 15 secondi. In questo modo, l'amministratore di sistema può distinguere tra problemi di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e problemi del sottosistema I/O. Il messaggio di errore 833 viene restituito e visualizzato nel log degli errori di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nel modo seguente:

`` 
SQL Server has encountered %d occurrence(s) of I/O requests taking longer than %d seconds to complete on file [%ls] in database [%ls] (%d). The OS file handle is 0x%p. The offset of the latest long I/O is: %#016I64x.
`` 

Un I/O lungo può essere un'operazione di lettura o scrittura. Questa indicazione non viene attualmente inclusa nel messaggio. I messaggi relativi a I/O lunghi sono avvisi e non messaggi di errore. Non indicano infatti problemi che si verificano in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ma vengono restituiti per consentire all'amministratore di sistema di individuare in modo più rapido la causa dei tempi di risposta lenti di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , nonché distinguere i problemi esterni al controllo di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. I messaggi relativi a I/O lunghi non richiedono quindi alcuna azione. È comunque consigliabile che l'amministratore di sistema verifichi il motivo per il quale per la richiesta di I/O è stato necessario un tempo così prolungato e se esso è giustificato.

#### <a name="causes-of-long-io-requests"></a>Cause delle richieste di I/O lunghi  
Un messaggio di I/O lungo indica che un I/O è bloccato definitivamente e non verrà mai completato (I/O perso) o semplicemente che non è stato ancora completato. Non è possibile capire dal messaggio di quale scenario si tratta, sebbene un I/O perso sia spesso causa di un timeout di latch.

Gli I/O lunghi indicano spesso un carico di lavoro di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] troppo intenso per il sottosistema disco. Le situazioni seguenti possono indicare un sottosistema disco non adeguato:

* Più messaggi di I/O lunghi vengono visualizzati nel log degli errori durante un carico di lavoro elevato di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .
* I contatori Perfmon indicano latenze prolungate del disco, lunghe code del disco o nessun tempo di inattività del disco.  

Gli I/O lunghi possono inoltre essere causati da un componente nel percorso di I/O (ad esempio, un driver, un controller o un firmware) che ritarda continuamente la risposta a una richiesta di I/O precedente privilegiando richieste più recenti, più vicine alla posizione corrente della testina. La tecnica comune di elaborazione delle richieste che dà priorità alle richieste più vicine alla posizione corrente della testina di lettura/scrittura è detta "accodamento dei comandi nativi". Questo può essere difficile da verificare mediante lo strumento Monitor di sistema di Windows (PERFMON.EXE) in quanto la maggioranza degli I/O vengono gestiti immediatamente. Le richieste di I/O lunghi possono essere ulteriormente complicate da carichi di lavoro che eseguono grandi quantità di I/O sequenziali, ad esempio backup e ripristino, analisi delle tabelle, ordinamento, creazione di indici, caricamenti bulk e azzeramento dei file.

Gli I/O lunghi isolati apparentemente non correlati a una delle condizioni precedenti possono essere causati da un problema hardware o di driver. Il log eventi di sistema può contenere un evento correlato che consente di individuare il problema.

#### <a name="error-detection"></a>Rilevamento degli errori  
Per le pagine di database sono disponibili due meccanismi facoltativi, ovvero la protezione delle pagine incomplete e la protezione dei checksum, che consentono di assicurare l'integrità della pagina dal momento in cui viene scritta sul disco fino a quando viene letta di nuovo. Questi meccanismi offrono una modalità indipendente di verifica della correttezza non solo dell'archiviazione dei dati, ma anche di componenti hardware quali controller, driver, cavi e perfino del sistema operativo. La protezione viene aggiunta alla pagina immediatamente prima della scrittura sul disco e viene verificata dopo la lettura della pagina dal disco.

#### <a name="torn-page-protection"></a>Protezione delle pagine incomplete  
La protezione delle pagine incomplete, disponibile in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000, rappresenta essenzialmente un modo di rilevare i danneggiamenti della pagina dovuti a interruzioni dell'alimentazione. Ad esempio, un'interruzione dell'alimentazione imprevista può fare sì che solo una parte di una pagina venga scritta su disco. Quando si utilizza la protezione delle pagine incomplete, alla fine di ogni settore da 512 byte della pagina viene inserita una firma a 2 bit (dopo aver copiato i due bit originali nell'intestazione di pagina). La firma alterna il binario 01 e 10 con ogni scrittura, pertanto è sempre possibile sapere quando solo una parte dei settori è stata scritta sul disco: se un bit si trova nello stato errato quando la pagina viene successivamente letta, la pagina è stata scritta correttamente e viene rilevata una pagina incompleta. Per il rilevamento delle pagine incomplete vengono utilizzate risorse minime, tuttavia non vengono rilevati tutti gli errori causati da problemi hardware del disco.

#### <a name="checksum-protection"></a>Protezione dei checksum  
La protezione dei checksum, disponibile in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005, offre una più solida funzionalità di verifica dell'integrità dei dati. Un checksum viene calcolato per i dati in ogni pagina scritta e archiviato nell'intestazione di pagina. Ogni volta che una pagina con un checksum archiviato viene letta dal disco, il motore di database ricalcola il checksum per i dati della pagina e genera un errore 824 se il nuovo checksum è diverso da quello archiviato. La protezione dei checksum è in grado di rilevare più errori rispetto alla protezione delle pagine incomplete in quanto dipende da ogni byte della pagina. Tuttavia, si tratta di un'operazione a moderato consumo di risorse. Quando il checksum è abilitato, gli errori causati da interruzioni dell'alimentazione e da hardware o firmware difettosi possono essere rilevati ogni volta che Gestione buffer legge una pagina dal disco.

Il tipo di protezione di pagina utilizzato è un attributo del database che contiene la pagina. La protezione dei checksum è la protezione predefinita per i database creati in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2005 e versioni successive. Il meccanismo di protezione di pagina viene specificato al momento della creazione del database e può essere modificato utilizzando ALTER DATABASE. È possibile determinare l'impostazione corrente per la protezione di pagina eseguendo una query nella colonna page_verify_option della vista del catalogo [sys.databases](../relational-databases/system-catalog-views/sys-databases-transact-sql.md) o nella proprietà IsTornPageDetectionEnabled della funzione [DATABASEPROPERTYEX](../t-sql/functions/databasepropertyex-transact-sql.md) . Se l'impostazione relativa alla protezione di pagina viene modificata, la nuova impostazione non viene immediatamente estesa all'intero database. Il livello di protezione del database corrente viene infatti esteso alle pagine a ogni successiva scrittura. Ciò significa che il database potrebbe essere costituito da pagine con tipi di protezione diversi. 

## <a name="understanding-non-uniform-memory-access"></a>Informazioni sull'architettura NUMA (Non-Uniform Memory Access)

Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supporta l'architettura NUMA (Non-Uniform Memory Access) e può essere utilizzato in modo efficace con hardware NUMA senza alcuna configurazione specifica. Con l'aumentare della velocità del clock e del numero di processori, diventa sempre più difficile ridurre la latenza di memoria necessaria per utilizzare questa ulteriore capacità di elaborazione. Per ovviare a questo problema, i fornitori di hardware offrono cache L3 di grandi dimensioni. Si tratta, tuttavia, di una soluzione soggetta a limiti. L'architettura NUMA offre una soluzione scalabile per questo problema. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è stato progettato per l'uso ottimale in computer basati su NUMA senza che sia necessario apportare alcuna modifica alle applicazioni. Per altre informazioni, vedere [Procedura: Configurazione di SQL Server per l'uso di Soft-NUMA](../database-engine/configure-windows/soft-numa-sql-server.md).

## <a name="see-also"></a>Vedere anche
[Lettura di pagine](../relational-databases/reading-pages.md)   
 [Scrittura di pagine](../relational-databases/writing-pages.md)


