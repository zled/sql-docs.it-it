---
title: Ambiente ospitato da Common Language Runtime | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- type-safe code [CLR integration]
- UNSAFE permission set
- run-time environments [CLR integration]
- common language runtime [SQL Server], about CLR integration
- application domains [CLR integration]
- host protection attributes [CLR integration]
- managed code [SQL Server], common language runtime
- permission sets [CLR integration]
- reliability [CLR integration]
- SAFE permission set
- code access security [CLR integration]
- EXTERNAL_ACCESS permission set
- verifying type safety
- scalability [CLR integration]
- hosted environments [CLR integration]
- HPAs [CLR integration]
ms.assetid: d280d359-08f0-47b5-a07e-67dd2a58ad73
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dbbc884a32f892830ec4b7b66e3a67c45fc37416
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129156"
---
# <a name="clr-hosted-environment"></a>Ambiente CLR
  CLR (Common Language Runtime) di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework è un ambiente che esegue molti linguaggi di programmazione attuali, inclusi [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic e [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C++. CLR include memoria sottoposta a Garbage Collection, threading preemptive, Servizio metadati (riflessione dei tipi), verificabilità del codice e sicurezza dall'accesso di codice. CLR utilizza metadati per individuare e caricare classi, disporre istanze in memoria, risolvere chiamate a metodi, generare codice nativo, implementare la sicurezza e impostare limiti di contesto per la fase di esecuzione.  
  
 CLR e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] differiscono come ambienti di esecuzione nelle modalità di gestione di memoria, thread e sincronizzazione. In questo argomento viene descritta l'integrazione tra questi due ambienti di esecuzione per consentire la gestione uniforme di tutte le risorse di sistema. In questo argomento viene inoltre descritta l'integrazione tra la sicurezza dall'accesso di codice di CLR e la sicurezza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per fornire un ambiente di esecuzione affidabile e protetto per il codice utente.  
  
## <a name="basic-concepts-of-clr-architecture"></a>Concetti di base dell'architettura CLR  
 In .NET Framework un programmatore scrive in un linguaggio di alto livello che implementa una classe definendone la struttura, ad esempio i campi o le proprietà della classe, e i metodi. Alcuni di questi metodi possono essere funzioni statiche. La compilazione del programma produce un file denominato assembly che contiene il codice compilato in MSIL ([!INCLUDE[msCoName](../../../includes/msconame-md.md)] Intermediate Language) e un manifesto che contiene tutti i riferimenti agli assembly dipendenti.  
  
> [!NOTE]  
>  Gli assembly sono un elemento essenziale nell'architettura di CLR, in quanto costituiscono le unità di compressione, distribuzione e controllo delle versioni del codice dell'applicazione in .NET Framework. Utilizzando gli assembly è possibile distribuire codice dell'applicazione nel database e garantire un metodo uniforme per amministrare, eseguire il backup e ripristinare applicazioni di database complete.  
  
 Il manifesto dell'assembly contiene metadati sull'assembly che descrivono tutti i campi, le strutture, le proprietà, le classi, le relazioni di ereditarietà, le funzioni e i metodi definiti nel programma. Il manifesto consente di stabilire l'identità dell'assembly, di specificare i file che costituiscono l'implementazione dell'assembly, di specificare i tipi e le risorse che compongono l'assembly, di rilevare le dipendenze in fase di compilazione da altri assembly e di specificare il set di autorizzazioni necessarie per la corretta esecuzione dell'assembly. Queste informazioni vengono utilizzate in fase di esecuzione per risolvere i riferimenti, applicare i criteri di associazione delle versioni e convalidare l'integrità degli assembly caricati.  
  
 .NET Framework supporta attributi personalizzati per l'annotazione di classi, proprietà, funzioni e metodi con informazioni aggiuntive che l'applicazione può acquisire nei metadati. Tutti i compilatori di .NET Framework utilizzano tali annotazioni senza interpretazione e le archiviano come metadati dell'assembly. Le annotazioni possono essere esaminate allo stesso modo di tutti gli altri metadati.  
  
 Il codice gestito viene eseguito da MSIL in CLR anziché direttamente dal sistema operativo. Le applicazioni con codice gestito acquisiscono i servizi CLR, quali operazioni automatiche di Garbage Collection, controllo dei tipi in fase di esecuzione, supporto della sicurezza e così via. Tali servizi consentono di garantire un comportamento uniforme e indipendente dalla piattaforma e dalla lingua per le applicazioni con codice gestito.  
  
## <a name="design-goals-of-clr-integration"></a>Obiettivi di progettazione dell'integrazione CLR  
 Quando il codice utente viene eseguito nell'ambiente CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], caratteristica denominata integrazione CLR, si applicano gli obiettivi di progettazione seguenti:  
  
###### <a name="reliability-safety"></a>Affidabilità (protezione)  
 Il codice utente non deve essere in grado di eseguire operazioni che danneggiano l'integrità dell'elaborazione del Motore di database, quali la visualizzazione di una finestra di messaggio popup in cui viene richiesta una risposta dell'utente o l'uscita dal processo. Il codice utente non deve essere in grado di sovrascrivere i buffer di memoria del Motore di database o le strutture di dati interne.  
  
###### <a name="scalability"></a>Scalabilità  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e CLR dispongono di modelli interni diversi per la pianificazione e la gestione della memoria. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta un modello di threading cooperativo in modalità non preemptive in cui i thread producono volontariamente l'esecuzione con frequenza periodica o quando sono in attesa di blocchi o I/O. CLR supporta un modello di threading preemptive. Se il codice utente in esecuzione in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] può chiamare direttamente le primitive di threading del sistema operativo, non si integra in modo soddisfacente nell'Utilità di pianificazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e può influire negativamente sulla scalabilità del sistema. CLR non distingue tra memoria virtuale e fisica, mentre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gestisce direttamente la memoria fisica e deve utilizzarla entro un limite configurabile.  
  
 I modelli diversi per threading, pianificazione e gestione della memoria presentano una sfida di integrazione per un sistema di gestione di database relazionali (RDBMS) con scalabilità in grado di supportare migliaia di sessioni utente simultanee. L'architettura deve garantire che la scalabilità del sistema non venga danneggiata dal codice utente che chiama direttamente le API per le primitive di threading, memoria e sincronizzazione.  
  
###### <a name="security"></a>Sicurezza  
 Il codice utente in esecuzione nel database deve essere conforme alle regole di autenticazione e autorizzazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in caso di accesso a oggetti di database, quali tabelle e colonne. Gli amministratori del database, inoltre, devono essere in grado di controllare l'accesso alle risorse del sistema operativo, ad esempio file e accesso di rete, dal codice utente in esecuzione nel database. Questo aspetto è importante in quanto i linguaggi di programmazione gestita, diversamente dai linguaggi non gestiti come Transact-SQL, forniscono API per accedere a tali risorse. Il sistema deve fornire un metodo protetto che consenta al codice utente di accedere alle risorse del computer al di fuori dell'elaborazione del [!INCLUDE[ssDE](../../../includes/ssde-md.md)]. Per altre informazioni, vedere [Sicurezza per l'integrazione con CLR](security/clr-integration-security.md).  
  
###### <a name="performance"></a>restazioni  
 Il codice utente gestito in esecuzione nel [!INCLUDE[ssDE](../../../includes/ssde-md.md)] deve offrire prestazioni computazionali analoghe allo stesso codice eseguito al di fuori del server. L'accesso ai database dal codice utente gestito non è rapido quanto [!INCLUDE[tsql](../../../includes/tsql-md.md)] nativo. Per altre informazioni, vedere [sulle prestazioni dell'integrazione con CLR](clr-integration-architecture-performance.md).  
  
## <a name="clr-services"></a>CLR Services  
 CLR fornisce un numero di servizi che semplificano la realizzazione degli obiettivi di progettazione dell'integrazione CLR con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
###### <a name="type-safety-verification"></a>Verifica dell'indipendenza dai tipi  
 Il codice indipendente dai tipi è un codice che accede alle strutture di memoria solo in modalità ben definite. Dato un riferimento a un oggetto valido, ad esempio, il codice indipendente dai tipi può accedere alla memoria solo a offset fissi corrispondenti ai membri di campo effettivi. Se, tuttavia, il codice accede alla memoria a offset arbitrari interni o esterni all'intervallo di memoria dell'oggetto, non si tratta di codice indipendente dai tipi. Quando gli assembly vengono caricati in CLR, prima che MSIL venga compilato tramite compilazione JIT (Just-In-Time), il runtime esegue una fase di verifica che esamina il codice per determinarne l'indipendenza dai tipi. Il codice che supera correttamente questa verifica viene denominato codice effettivamente indipendente dai tipi.  
  
###### <a name="application-domains"></a>Domini applicazione  
 CLR supporta il concetto di domini applicazione come aree di esecuzione all'interno di un processo host in cui è possibile caricare ed eseguire assembly di codice gestito. Il confine del dominio applicazione fornisce isolamento tra assembly. Gli assembly sono isolati in termini di visibilità di variabili statiche e membri di dati e di possibilità di chiamare codice dinamicamente. I domini applicazione costituiscono inoltre il meccanismo per caricare e scaricare codice. Il codice può essere scaricato dalla memoria solo scaricando il dominio applicazione. Per altre informazioni, vedere [domini applicazione e sicurezza dell'integrazione CLR](../../database-engine/dev-guide/application-domains-and-clr-integration-security.md).  
  
###### <a name="code-access-security-cas"></a>Sicurezza dall'accesso di codice (CAS, Code Access Security)  
 Il sistema di sicurezza CLR fornisce un metodo per determinare i possibili tipi di operazioni eseguite dal codice gestito tramite l'assegnazione di autorizzazioni al codice. Le autorizzazioni di accesso per il codice vengono assegnate in base all'identità del codice, ad esempio la firma dell'assembly o l'origine del codice.  
  
 CLR fornisce criteri a livello di computer che possono essere impostati dall'amministratore del computer. Tali criteri definiscono le autorizzazioni concesse per qualsiasi codice gestito in esecuzione nel computer. Vi sono inoltre criteri di sicurezza a livello di host che possono essere utilizzati dagli host, ad esempio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], per specificare restrizioni aggiuntive per il codice gestito.  
  
 Se un'API gestita in .NET Framework espone operazioni in risorse protette da un'autorizzazione di accesso per il codice, l'API richiederà tale autorizzazione prima di accedere alla risorsa. Questa richiesta fa in modo che il sistema di sicurezza CLR attivi un controllo completo di ogni unità di codice (assembly) nello stack di chiamate. Verrà concesso l'accesso alla risorsa solo se l'intera sequenza delle chiamate dispone dell'autorizzazione.  
  
 Si noti che la possibilità di generare dinamicamente codice gestito tramite l'API Reflection.Emit non è supportata all'interno dell'ambiente CLR in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Tale codice non disporrebbe delle autorizzazioni di protezione dall'accesso di codice per l'esecuzione e avrebbe quindi esito negativo in fase di esecuzione. Per altre informazioni, vedere [CLR Integration Code Access Security](security/clr-integration-code-access-security.md).  
  
###### <a name="host-protection-attributes-hpas"></a>Attributi di protezione host  
 CLR fornisce un meccanismo per annotare API gestite che fanno parte di .NET Framework con determinati attributi che possono interessare un host di CLR. Tra gli esempi di tali attributi sono inclusi i seguenti:  
  
-   SharedState, che indica se l'API espone la possibilità di creare o gestire stato condiviso, ad esempio campi classe statici.  
  
-   Synchronization, che indica se l'API espone la possibilità di eseguire la sincronizzazione tra thread.  
  
-   ExternalProcessMgmt, che indica se l'API espone una modalità per controllare il processo host.  
  
 Tramite questi attributi l'host può specificare un elenco di attributi di protezione host, ad esempio l'attributo SharedState, che non devono essere consentiti nell'ambiente host. In tal caso, CLR rifiuta i tentativi da parte del codice utente di chiamare API annotate tramite attributi di protezione host inclusi nell'elenco degli attributi non consentiti. Per altre informazioni, vedere [attributi di protezione Host e programmazione di integrazione CLR](../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md).  
  
## <a name="how-sql-server-and-the-clr-work-together"></a>Funzionamento dell'integrazione tra SQL Server e CLR  
 In questa sezione viene illustrata l'integrazione in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dei modelli di threading, di pianificazione, di sincronizzazione e di gestione della memoria di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e CLR. In particolare, in questa sezione viene esaminata l'integrazione alla luce di obiettivi di scalabilità, affidabilità e sicurezza. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] essenzialmente è utilizzato come sistema operativo per CLR quando è ospitato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. CLR chiama routine di basso livello implementate da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per il threading, la pianificazione, la sincronizzazione e la gestione della memoria. Si tratta delle stesse primitive utilizzate dal resto del motore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Questo approccio offre diversi vantaggi correlati a scalabilità, affidabilità e sicurezza.  
  
###### <a name="scalability-common-threading-scheduling-and-synchronization"></a>Scalabilità: threading, pianificazione e sincronizzazione comuni  
 CLR chiama le API di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per la creazione di thread, sia per l'esecuzione del codice utente sia per uso interno. Ai fini della sincronizzazione tra più thread, CLR chiama gli oggetti di sincronizzazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ciò consente all'utilità di pianificazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di pianificare altre attività quando un thread è in attesa di un oggetto di sincronizzazione. Quando, ad esempio, CLR avvia la procedura di Garbage Collection, tutti i relativi thread sono in attesa del completamento di tale procedura. Poiché i thread CLR e gli oggetti di sincronizzazione di cui sono in attesa vengono rilevati dall'utilità di pianificazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] può pianificare thread che eseguono altre attività del database che non interessano CLR. Ciò consente inoltre a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di rilevare deadlock che comportano blocchi acquisiti da oggetti di sincronizzazione CLR e di utilizzare tecniche tradizionali per la rimozione di tali deadlock.  
  
 Il codice gestito viene eseguito in modalità preemptive in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. L'utilità di pianificazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è in grado di rilevare e arrestare i thread non eseguiti per una quantità di tempo significativa. La possibilità di eseguire hook di thread CLR a thread di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] implica che l'utilità di pianificazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sia in grado di identificare i thread sfuggiti al controllo in CLR e di gestirne la priorità. Tali thread sfuggiti al controllo vengono sospesi e reinseriti nella coda. I thread identificati ripetutamente come thread sfuggiti al controllo non possono essere eseguiti per un determinato periodo di tempo, in modo da consentire l'esecuzione di altri thread worker.  
  
> [!NOTE]  
>  Il codice gestito con esecuzione prolungata che accede ai dati o alloca memoria sufficiente per attivare la procedura di Garbage Collection viene restituito automaticamente. Il codice gestito con esecuzione prolungata che non accede ai dati né alloca memoria gestita sufficiente per attivare la procedura di Garbage Collection deve essere restituito in modo esplicito chiamando la funzione System.Thread.Sleep() di .NET Framework.  
  
###### <a name="scalability-common-memory-management"></a>Scalabilità: gestione della memoria comune  
 CLR chiama primitive di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per allocare e deallocare la memoria. Poiché la memoria utilizzata da CLR viene rilevata nell'utilizzo di memoria totale del sistema, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è in grado di rispettare i limiti di memoria configurati e di garantire che CLR e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stesso non creino conflitti di memoria reciproci. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] può anche rifiutare le richieste di memoria CLR quando la memoria di sistema è vincolata, e può chiedere a CLR di ridurre l'utilizzo della memoria quando le altre attività hanno bisogno memoria.  
  
###### <a name="reliability-application-domains-and-unrecoverable-exceptions"></a>Affidabilità: domini applicazione ed eccezioni irreversibili  
 Quando il codice gestito nelle API di .NET Framework rileva eccezioni critiche, ad esempio un errore di memoria insufficiente o di overflow dello stack, non è sempre possibile recuperare il sistema e garantire semantica coerente e corretta per l'implementazione. Le API generano un'eccezione di interruzione del thread in risposta a tali errori.  
  
 Se ospitate in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], tali interruzioni del thread vengono gestite nel modo seguente: CLR rileva qualsiasi stato condiviso nel dominio applicazione in cui si verifica l'interruzione del thread. A tale scopo, CLR verifica l'eventuale presenza di oggetti di sincronizzazione. Se è presente uno stato condiviso nel dominio applicazione, viene scaricato il dominio applicazione stesso. Lo scaricamento del dominio applicazione comporta l'arresto delle transazioni del database in esecuzione nel dominio applicazione. Poiché la presenza dello stato condiviso può aumentare l'impatto di tali eccezioni critiche sulle sessioni utente diverse da quella che ha attivato l'eccezione, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e CLR sono state introdotte procedure per ridurre la probabilità del verificarsi di tale stato. Per ulteriori informazioni, vedere la documentazione di .NET Framework.  
  
###### <a name="security-permission-sets"></a>Sicurezza: set di autorizzazioni  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] consente agli utenti di specificare i requisiti di affidabilità e sicurezza per il codice distribuito nel database. Una volta caricati gli assembly nel database, l'autore dell'assembly può specificare uno tra i tre set di autorizzazioni per l'assembly seguenti: SAFE, EXTERNAL_ACCESS e UNSAFE.  
  
|||||  
|-|-|-|-|  
|Set di autorizzazioni|SAFE|EXTERNAL_ACCESS|UNSAFE|  
|Sicurezza dall'accesso di codice|Sola esecuzione|Esecuzione più accesso a risorse esterne|Senza restrizioni|  
|Restrizioni del modello di programmazione|Sì|Sì|Nessuna restrizione|  
|Requisito di verificabilità|Sì|Sì|no|  
|Possibilità di chiamare il codice nativo|no|no|Sì|  
  
 Grazie alle restrizioni associate in termini di modello di programmazione consentito, SAFE rappresenta la modalità più affidabile e protetta. Gli assembly SAFE dispongono di autorizzazioni sufficienti per l'esecuzione, l'elaborazione di calcoli e l'accesso al database locale. Gli assembly SAFE devono essere effettivamente indipendenti dai tipi e non possono chiamare codice non gestito.  
  
 UNSAFE è un set di autorizzazioni per codice altamente attendibile, che può essere creato solo dagli amministratori di database. Questo codice attendibile non presenta restrizioni di sicurezza dall'accesso di codice e può chiamare codice non gestito (nativo).  
  
 EXTERNAL_ACCESS fornisce un'opzione di sicurezza intermedia e consente al codice di accedere alle risorse esterne al database, offrendo lo stesso livello di affidabilità di SAFE.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizza il livello dei criteri di protezione dall'accesso di codice a livello di host per configurare un criterio host che concede uno dei tre set di autorizzazioni in base all'autorizzazione archiviata nei cataloghi di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il codice gestito in esecuzione all'interno del database ottiene sempre uno di questi set di autorizzazioni di accesso per il codice.  
  
### <a name="programming-model-restrictions"></a>Restrizioni del modello di programmazione  
 Il modello di programmazione per il codice gestito in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] comporta la scrittura di funzioni, procedure e tipi che in genere non richiedono l'utilizzo dello stato gestito tra più chiamate né la condivisione dello stato tra più sessioni utente. Come descritto in precedenza, la presenza dello stato condiviso può inoltre determinare eccezioni critiche che influiscono sulla scalabilità e l'affidabilità dell'applicazione.  
  
 Considerati questi aspetti, non è consigliabile utilizzare variabili statiche e membri di dati statici di classi utilizzate in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per gli assembly SAFE ed EXTERNAL_ACCESS, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esamina i metadati dell'assembly durante la fase CREATE ASSEMBLY e, se rileva l'utilizzo di variabili e membri di dati statici, impedisce la creazione di tali assembly.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] impedisce inoltre le chiamate ad API di .NET Framework annotate tramite gli attributi di protezione host `SharedState`, `Synchronization` e `ExternalProcessMgmt`. In questo modo, viene impedito agli assembly SAFE ed EXTERNAL_ACCESS di chiamare qualsiasi API che consente la condivisione dello stato, di eseguire la sincronizzazione e di influire sull'integrità del processo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per altre informazioni, vedere [restrizioni del modello di programmazione integrazione CLR](database-objects/clr-integration-programming-model-restrictions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza dell'integrazione CLR](security/clr-integration-security.md)   
 [Prestazioni dell'integrazione con CLR](clr-integration-architecture-performance.md)  
  
  
