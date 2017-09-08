---
title: Governance delle risorse per R Services | Microsoft Docs
ms.custom: 
ms.date: 05/31/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18c9978a-aa55-42bd-9ab3-8097030888c9
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5475c2258971c48c2e19bba69d9ec962ae48be87
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="resource-governance-for-r-services"></a>Governance delle risorse per R Services
  Un punto debole di R è rappresentato dal fatto che l'analisi di grandi quantità di dati nell'ambiente di produzione richiede hardware aggiuntivo e i dati vengono spesso spostati al di fuori del database in computer non controllati dall'IT.  Per eseguire operazioni di analisi avanzata, i clienti vogliono sfruttare le risorse dei server di database e per proteggere i dati è necessario che tali operazioni soddisfino requisiti di conformità di livello aziendale, ad esempio per quanto riguarda sicurezza e prestazioni.  
  
 Questa sezione fornisce informazioni su come gestire le risorse usate dal runtime R e dai processi R in esecuzione con un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] come contesto di calcolo.  
  
## <a name="what-is-resource-governance"></a>Informazioni sulla governance delle risorse  
 La governance delle risorse è progettata per identificare e prevenire i problemi comuni in un ambiente server di database, in cui ci sono spesso più applicazioni dipendenti e più servizi da supportare e bilanciare. Per [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], la governance delle risorse include le attività seguenti:  
  
-   Identificazione di script che usano una quantità eccessiva di risorse del server.  
  
     L'amministratore deve poter terminare o limitare i processi che utilizzano troppe risorse.  
  
-   Riduzione dei carichi di lavoro imprevedibili.  
  
     Se, ad esempio, più processi R sono in esecuzione simultaneamente sul server e tali processi non sono isolati uno dall'altro tramite pool di risorse, la contesa per le risorse risultante potrebbe comportare prestazioni imprevedibili o compromettere il completamento del carico di lavoro.  
  
-   Assegnazione di priorità ai carichi di lavoro.  
  
     L'amministratore o il progettista deve poter specificare i carichi di lavoro che hanno la precedenza o garantire il completamento di determinati carichi di lavoro in caso di contesa per le risorse.  
  
 In [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è possibile usare [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) per gestire le risorse usate dal runtime R e dai processi R remoti.  
  
## <a name="how-to-use-resource-governor-to-manage-r-jobs"></a>Come usare Resource Governor per gestire i processi R  
 In generale, è possibile gestire le risorse allocate ai processi R creando *pool di risorse esterne* e assegnando carichi di lavoro ai pool. Un pool di risorse esterne è un nuovo tipo di pool di risorse introdotto in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per supportare la gestione del runtime R e di altri processi esterni al motore di database.  
  
 In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ci sono ora tre tipi di pool di risorse predefiniti.  
  
-   Il *pool interno* rappresenta le risorse usate da SQL Server e non può essere modificato o limitato.  
  
-   Il *pool predefinito* è un pool di utenti predefinito che è possibile usare per modificare l'uso delle risorse per il server nel complesso. È anche possibile definire gruppi di utenti che appartengono al pool, per gestire l'accesso alle risorse.  
  
-   Il *pool esterno predefinito* è un pool di utenti predefinito per le risorse esterne. È anche possibile creare un nuovo pool di risorse esterne e definire i gruppi di utenti che appartengono a questo pool.  
  
 Inoltre, è possibile creare *pool di risorse definiti dall'utente* per allocare le risorse al motore di database o ad altre applicazioni e creare *pool di risorse esterne definiti dall'utente* per gestire R e altri processi esterni.  
  
 Per una buona introduzione ai concetti generali e alla terminologia, vedere [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md).  

  
## <a name="resource-management-using-resource-governor"></a>Gestione delle risorse con Resource Governor 

   Se non si conosce Resource Governor, vedere questo argomento per una rapida procedura dettagliata su come modificare le risorse predefinite dell'istanza e creare un nuovo pool di risorse esterne: [Procedura: Creare un pool di risorse per R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)   
  
 È possibile usare il meccanismo di *pool di risorse esterne* per gestire le risorse usate dai file eseguibili R seguenti:  
  
-   Rterm.exe e processi satellite  
  
-   BxlServer.exe e processi satellite  
  
-   Processi satellite avviati da LaunchPad  
  
 La gestione diretta del servizio Launchpad con Resource Governor non è tuttavia supportata. Ciò accade perché [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] è un servizio attendibile che da progettazione può ospitare solo utilità di avvio fornite da Microsoft. Le utilità di avvio attendibili sono inoltre configurate per evitare l'utilizzo eccessivo di risorse.  
  
 È consigliabile gestire i processi satellite tramite Resource Governor e ottimizzarli in modo da soddisfare le esigenze del carico di lavoro e della configurazione del database specifico.  Qualsiasi processo satellite, ad esempio, può essere creato o eliminato definitivamente on demand durante l'esecuzione.  
  
## <a name="disable-external-script-execution"></a>Disabilitare l'esecuzione di script esterni  
 Il supporto per gli script esterni è facoltativo nell'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Anche dopo l'installazione di [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)], la possibilità di eseguire script esterni è disattivata per impostazione predefinita e per abilitare l'esecuzione di script è necessario riconfigurare manualmente la proprietà e riavviare l'istanza.  
  
 Se quindi c'è un problema di risorse o di sicurezza che deve essere risolto rapidamente, un amministratore può disabilitare immediatamente l'esecuzione di script esterni usando [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) e impostando la proprietà `external scripts enabled` su FALSE o 0.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione e monitoraggio di soluzioni R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
 [Procedura: Creare un pool di risorse per R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)  
 [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)
  


