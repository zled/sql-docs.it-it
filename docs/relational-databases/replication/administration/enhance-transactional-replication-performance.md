---
title: Migliorare le prestazioni della replica transazionale | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- performance [SQL Server replication], transactional replication
- designing databases [SQL Server], replication performance
- performance [SQL Server replication], snapshot replication
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- Distribution Agent, performance
- transactional replication, performance
- Log Reader Agent, performance
ms.assetid: 67084a67-43ff-4065-987a-3b16d1841565
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e503b9cda54099a4fa283f3ef26747b9d5c9bd9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enhance-transactional-replication-performance"></a>Miglioramento delle prestazioni della replica transazionale
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Dopo aver considerato i suggerimenti sulle prestazioni generali descritti nella sezione [Miglioramento delle prestazioni generali della replica](../../../relational-databases/replication/administration/enhance-general-replication-performance.md), tenere presente le aree aggiuntive specifiche della replica transazionale riportate di seguito.  
  
## <a name="database-design"></a>Progettazione di database  
  
-   Ridurre al minimo le dimensioni delle transazioni nella progettazione delle applicazioni.  
  
     Per impostazione predefinita, la replica transazionale propaga le modifiche in base ai limiti delle transazioni. Più piccole sono le transazioni, minori saranno le probabilità che l'agente di distribuzione dovrà rinviare una transazione a causa di problemi di rete. Se è necessario che l'agente rinvii una transazione, la quantità di dati inviati sarà inferiore.  
  
## <a name="distributor-configuration"></a>Configurazione del server di distribuzione  
  
-   Configurare il server di distribuzione in un server dedicato.  
  
     È possibile ridurre l'overhead di elaborazione sul server di pubblicazione configurando un server di distribuzione remoto. Per altre informazioni, vedere [Configure Distribution](../../../relational-databases/replication/configure-distribution.md).  
  
-   Ridimensionare in modo appropriato il database di distribuzione.  
  
     Verificare la replica con un carico tipico per il sistema per determinare lo spazio necessario per archiviare i comandi. Verificare che il database sia sufficientemente grande da consentire l'archiviazione dei comandi senza richiedere un aumento automatico delle dimensioni frequente. Per altre informazioni sulla modifica delle dimensioni di un database, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="publication-design"></a>Progettazione della pubblicazione  
  
-   Replicare l'esecuzione della stored procedure durante gli aggiornamenti batch delle tabelle pubblicate.  
  
     In caso di aggiornamenti batch che occasionalmente interessano un numero di righe elevato nel Sottoscrittore, è possibile aggiornare la tabella pubblicata utilizzando una stored procedure di cui quindi verrà pubblicata l'esecuzione. Anziché inviare un aggiornamento o un'eliminazione per ogni riga interessata, l'agente di distribuzione esegue la stessa procedura nel Sottoscrittore utilizzando valori dei parametri identici. Per altre informazioni, vedere [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md).  
  
-   Distribuire gli articoli in più pubblicazioni.  
  
     Se non è possibile utilizzare il parametro **-SubscriptionStreams** , descritto più avanti in questo argomento, provare a creare più pubblicazioni. La distribuzione di articoli tra queste pubblicazioni consente alla replica di applicare le modifiche in parallelo con i Sottoscrittori.  
  
## <a name="subscription-considerations"></a>Considerazioni sulle sottoscrizioni  
  
-   Utilizzare agenti indipendenti anziché agenti condivisi se si dispone di più pubblicazioni nello stesso server di pubblicazione, in base all'impostazione predefinita di Creazione guidata nuova pubblicazione.  
  
-   Eseguire gli agenti in modo continuo anziché pianificarne l'esecuzione con frequenza elevata.  
  
     L'impostazione di un'esecuzione continua degli agenti anziché la creazione di pianificazioni frequenti, ad esempio ogni minuto, consente di migliorare le prestazioni della replica in quanto non richiede l'avvio e l'arresto dell'agente. Quando si imposta l'esecuzione continua dell'agente di distribuzione, le modifiche vengono propagate con una bassa latenza agli altri server connessi nella topologia. Per altre informazioni, vedere:  
  
    -   [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]: [Specificare le pianificazioni della sincronizzazione](../../../relational-databases/replication/specify-synchronization-schedules.md)  
  
## <a name="distribution-agent-and-log-reader-agent-parameters"></a>Parametri dell'agente di distribuzione e dell'agente di lettura log  
  
-   Per risolvere i colli di bottiglia accidentali, usare il parametro **–MaxCmdsInTran** per l'agente di lettura log.  
  
     Il parametro **–MaxCmdsInTran** specifica il numero massimo di istruzioni raggruppate in una transazione mentre l'agente di lettura log scrive i comandi nel database di distribuzione. L'utilizzo di questo parametro consente all'agente di lettura log e all'agente di distribuzione di dividere le transazioni di grandi dimensioni, ovvero costituite da molti comandi, nel server di pubblicazione in diverse transazioni più piccole quando i comandi vengono applicati al Sottoscrittore. Può inoltre ridurre la possibilità che si verifichino contese nel server di distribuzione e diminuire la latenza tra il server di pubblicazione e il Sottoscrittore. Dal momento che la transazione originale viene applicata in unità più piccole, il Sottoscrittore può accedere alle righe di una vasta transazione logica del server di pubblicazione prima della fine della transazione originale, violando la rigida atomicità transazionale. Il valore predefinito è **0**, che consente di mantenere i limiti delle transazioni del server di pubblicazione. Questo parametro non è applicabile ai server di pubblicazione Oracle.  
  
    > [!WARNING]  
    >  **MaxCmdsInTran** non è stato progettato per essere sempre abilitato. Sono disponibili casi di risoluzione in cui qualcuno ha accidentalmente eseguito un numero elevato di operazioni DML in una singola transazione (causando ritardi nella distribuzione dei comandi fino a che l'intera transazione è in database di distribuzione, blocchi mantenuti e così via). Se periodicamente si verifica questa situazione, è necessario esaminare le applicazioni e trovare un modo per ridurre le dimensioni della transazione.  
  
-   usare il parametro **–SubscriptionStreams** per l'agente di distribuzione.  
  
     Il parametro **–SubscriptionStreams** può migliorare notevolmente la velocità effettiva della replica aggregata. e consente a più connessioni a un Sottoscrittore l'applicazione di batch di modifiche in parallelo, conservando molte delle caratteristiche transazionali disponibili quando si utilizza un singolo thread. Se si verifica un errore di esecuzione o di commit di una delle connessioni, tutte le connessioni interromperanno il batch corrente e l'agente utilizzerà un singolo flusso per ripetere i batch non riusciti. Prima del completamento di questa fase di tentativi, possono verificarsi inconsistenze temporanee delle transazioni nel Sottoscrittore. Al termine del commit dei batch non riusciti, viene ripristinata la consistenza delle transazioni nel Sottoscrittore.  
  
     È possibile specificare un valore per questo parametro di agente usando **@subscriptionstreams** di [sp_addsubscription &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md).  
  
-   Aumentare il valore del parametro **-ReadBatchSize** per l'agente di lettura log.  
  
     L'agente di lettura log e l'agente di distribuzione supportano le dimensioni di batch per operazioni di lettura e commit delle transazioni. Per impostazione predefinita, le dimensioni del batch sono pari a 500 transazioni. L'agente di lettura log legge il numero specifico di transazioni nel log, indipendentemente dal fatto che siano contrassegnate o meno per la replica. Se in un database di pubblicazione viene scritto un numero elevato di transazioni, ma solo un subset ridotto è contrassegnato per la replica, è necessario usare il parametro **-ReadBatchSize** per aumentare la dimensione del batch di lettura dell'agente di lettura log. Questo parametro non è applicabile ai server di pubblicazione Oracle.  
  
-   Aumentare il valore del parametro **-CommitBatchSize** per l'agente di distribuzione.  
  
     Il commit di un set di transazioni presenta un overhead fisso. Se si esegue il commit di un numero maggiore di transazioni con una frequenza minore, l'overhead viene distribuito in un volume più ampio di dati. Tuttavia, il vantaggio offerto dall'aumento del valore di questo parametro decade in quanto il costo dell'applicazione delle modifiche è controllato da altri fattori, come l'I/O massimo del disco che contiene il log. È inoltre necessario tenere presente che gli errori che determinano l'avvio dell'agente di distribuzione richiedono l'esecuzione del rollback e la nuova applicazione di un numero maggiore di transazioni. Per le reti non affidabili, un valore più basso può generare meno errori nonché il rollback e la riapplicazione di un numero inferiore di transazioni in caso di errore.  
  
-   Ridurre il valore del parametro **-PollingInterval** per l'agente di lettura log.  
  
     Il parametro **-PollingInterval** specifica la frequenza con cui viene eseguita la query sulle transazioni da replicare nel log delle transazioni di un database pubblicato. Il valore predefinito è 5 secondi. Se si riduce tale valore, il polling del log viene eseguito più spesso con la possibilità di generare una latenza più bassa per il recapito delle transazioni dal database di pubblicazione nel database di distribuzione. È tuttavia consigliabile valutare la necessità di una latenza più bassa rispetto a un carico maggiore sul server determinato dall'esecuzione più frequente del polling.  
  
 I parametri degli agenti possono essere specificati nei profili agente e dalla riga di comando. Per altre informazioni, vedere:  
  
-   [Usare i profili agenti di replica](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)  
  
-   [Visualizzare e modificare i parametri del prompt dei comandi dell'agente di replica &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   [Replication Agent Executables Concepts](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
  
