---
title: Governance delle risorse per machine learning in SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: abe130ef7e465326999e0c71ce01e88dfa6269a3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31202463"
---
# <a name="resource-governance-for-machine-learning-in-sql-server"></a>Governance delle risorse per machine learning in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fornisce una panoramica di governance delle risorse di funzionalità di SQL Server che consentono di allocare e bilanciare le risorse utilizzate dagli script R e Python.

**Si applica a:** [!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)]
[!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] e [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]

## <a name="goals-of-resource-governance-for-machine-learning"></a>Obiettivi di governance delle risorse per machine learning

Un punto di problemi noti con linguaggi di machine learning, ad esempio R e Python è che i dati vengono spesso spostati all'esterno del database ai computer non controllati da IT. Un vantaggio è che R è a thread singolo, vale a dire che è possibile utilizzare solo con i dati disponibili in memoria. 

Servizi di SQL Server Machine Learning riduce entrambi questi problemi, e consente di soddisfano i requisiti di conformità dell'organizzazione. Consente di mantenere analitica avanzati all'interno del database e supporta miglioramento delle prestazioni su grandi set di dati tramite le funzionalità, ad esempio il flusso e operazioni di suddivisione in blocchi. Tuttavia, lo spostamento di R e Python calcoli all'interno di database di influire sulle prestazioni di altri servizi che utilizzano il database, tra cui query utente normale, le applicazioni esterne e i processi pianificati del database.

In questa sezione fornisce informazioni su come è possibile gestire le risorse utilizzate dal runtime esterni, ad esempio R e Python, per ridurre l'impatto su altri servizi di database principale. Un ambiente server di database è in genere l'hub per più servizi e applicazioni dipendenti.

È possibile utilizzare [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) per gestire le risorse utilizzate dal runtime esterni per R e Python.  Per l'apprendimento automatico, la governance delle risorse include le attività:

+ Identificazione di script che usano una quantità eccessiva di risorse del server.
  
     L'amministratore deve poter terminare o limitare i processi che utilizzano troppe risorse.
  
+ Riduzione dei carichi di lavoro imprevedibili.
  
     Ad esempio, se più processi di machine learning eseguono contemporaneamente sul server, la contesa tra risorse risultante potrebbe comportare prestazioni imprevedibile o compromettere il completamento del carico di lavoro. Tuttavia, se vengono utilizzati pool di risorse, i processi possono essere isolati una da altra.
  
-   Assegnazione di priorità ai carichi di lavoro.
  
     L'amministratore o un architetto deve essere in grado di specificare i carichi di lavoro che deve hanno la precedenza o garantire la contesa tra risorse è necessario completare alcuni carichi di lavoro.

## <a name="how-to-use-resource-governor-to-manage-machine-learning"></a>Come utilizzare Resource Governor per gestire l'apprendimento
 
Gestire le risorse allocate alle sessioni di R o Python mediante la creazione di un *pool di risorse esterne*e l'assegnazione di carichi di lavoro per il pool o il pool. Un pool di risorse esterne è un nuovo tipo di pool di risorse introdotta in [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] per gestire il runtime di R e altri processi esterni al motore di database.

SQL Server supporta tre tipi di pool di risorse predefiniti: 
  
-   Il *pool interno* rappresenta le risorse usate da SQL Server e non può essere modificato o limitato.
  
-   Il *pool predefinito* è un pool di utenti predefinito che è possibile usare per modificare l'uso delle risorse per il server nel complesso. È anche possibile definire gruppi di utenti che appartengono al pool, per gestire l'accesso alle risorse.
  
-   Il *pool esterno predefinito* è un pool di utenti predefinito per le risorse esterne. È anche possibile creare un nuovo pool di risorse esterne e definire i gruppi di utenti che appartengono a questo pool.
  
 Inoltre, è possibile creare *pool di risorse definiti dall'utente* per allocare le risorse al motore di database o ad altre applicazioni e creare *pool di risorse esterne definiti dall'utente* per gestire R e altri processi esterni.
  
 Per una buona introduzione ai concetti generali e alla terminologia, vedere [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md).

  
## <a name="resource-management-walkthrough-with-resource-governor"></a>Procedura dettagliata di gestione di risorse con Resource Governor

Se si ha familiarità di Resource Governor, vedere l'argomento per una rapida procedura dettagliata per modificare le risorse predefinite di istanza e creare un nuovo pool di risorse esterne: [creare un pool di risorse per gli script esterni](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)
  
 È possibile utilizzare il *pool di risorse esterne* meccanismo per gestire le risorse usate dai seguenti file eseguibili che vengono usati in machine learning:

+ Rterm.exe e processi satellite
+ Processi Python.exe e satellite
+ BxlServer.exe e processi satellite
+ Processi satellite avviati dalla finestra di avvio
  
> [!NOTE]
> 
> Non è supportata la gestione diretta del servizio Launchpad tramite Resource Governor. Ciò accade perché [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] è un servizio attendibile che da progettazione può ospitare solo utilità di avvio fornite da Microsoft. Avvio attendibili è configurati per evitare un utilizzo eccessivo di risorse.
>   
> È consigliabile gestire i processi satellite tramite Resource Governor e ottimizzarli in modo da soddisfare le esigenze del carico di lavoro e della configurazione del database specifico.  Qualsiasi processo satellite, ad esempio, può essere creato o eliminato definitivamente on demand durante l'esecuzione.
  
## <a name="disable-external-script-execution"></a>Disabilitare l'esecuzione dello script esterno

Il supporto per gli script esterni è facoltativo nell'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Anche dopo l'installazione di machine learning funzionalità, la possibilità di eseguire gli script esterni è impostata su OFF per impostazione predefinita e manualmente necessario riconfigurare le proprietà e riavviare l'istanza per consentire l'esecuzione dello script.

Pertanto, se si verifica un problema della risorsa che deve essere risolti immediatamente o un problema di sicurezza, un amministratore può immediatamente disabilitare qualsiasi esecuzione dello script esterno usando [sp_configure &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) e impostando la proprietà `external scripts enabled` su FALSE o 0.
  
## <a name="see-also"></a>Vedere anche

[Gestione e monitoraggio delle soluzioni di apprendimento automatico](../../advanced-analytics/r/managing-and-monitoring-r-solutions.md)

[Creare un pool di risorse per Machine Learning](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)

[Pool di risorse](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
