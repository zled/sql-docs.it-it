---
title: Governance delle risorse per Python | Documenti Microsoft
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1fff94725d1e564b4fe9eb286ea6bf1e390a3179
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="resource-governance-for-python"></a>Governance delle risorse per Python

Poiché Python viene abilitato tramite la stessa architettura di estendibilità implementate per il linguaggio R in SQL Server 2016, utilizzare gli strumenti esistenti in SQL Server, ad esempio Resource Governor e viste a gestione dinamica degli eventi estesi, per monitorare l'esecuzione di Python script in SQL Server.

Governance delle risorse, in particolare, è importante perché l'analisi di grandi quantità di dati nell'ambiente di produzione può determinare il hardware anche avanzata.  Per evitare dati spostati all'esterno del database per i computer che potrebbero non essere gestiti o controllati, è importante che l'amministratore del database alloca risorse sufficienti per le operazioni avanzate analitica.

In questa sezione vengono fornite informazioni su come è possibile gestire le risorse utilizzate dal runtime di Python e monitorare l'utilizzo delle risorse da Python script dei processi in esecuzione nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.

> [!NOTE]
> Supporto Python è una nuova funzionalità di SQL Server 2017 ed è in versione provvisoria. Per ulteriori informazioni appena, vedere.
> In generale, è possibile monitorare qualsiasi script esterni, inclusi uno che esegue Python, usando lo stesso framework fornito per la governance delle risorse di script R in SQL Server 2016.

## <a name="what-is-resource-governance"></a>Informazioni sulla governance delle risorse

La governance delle risorse è progettata per identificare e prevenire i problemi comuni in un ambiente server di database, in cui ci sono spesso più applicazioni dipendenti e più servizi da supportare e bilanciare. Per [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], la governance delle risorse include le attività seguenti:  

+ **Identificazione di script che utilizzano le risorse del server eccessivo**. L'amministratore deve poter terminare o limitare i processi che utilizzano troppe risorse.

+ **Riduzione dei carichi di lavoro imprevedibile**. Se più processi di Python sono in esecuzione contemporaneamente sul server e i processi non sono isolati tra loro tramite pool di risorse, la contesa tra risorse risultante potrebbe comportare prestazioni imprevedibile o compromettere il completamento del carico di lavoro.

+ **Assegnazione di priorità ai carichi di lavoro**. L'amministratore o il progettista deve poter specificare i carichi di lavoro che hanno la precedenza o garantire il completamento di determinati carichi di lavoro in caso di contesa per le risorse.

È possibile utilizzare [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) per gestire le risorse utilizzate dal runtime esterni. Sono inclusi script Python che vengono avviati da un remoto terminal ma eseguito utilizzando il computer SQL Server come contesto di calcolo.

> [!NOTE] 
> Resource Governor è disponibile in Enterprise Edition.

## <a name="how-to-use-resource-governor-to-manage-python-execution"></a>Come utilizzare Resource Governor per gestire l'esecuzione di Python

In generale, gestire le risorse allocate a qualsiasi processo di script esterni, creando un *pool di risorse esterne* e l'assegnazione di carichi di lavoro al pool. Un pool di risorse esterne è un nuovo tipo di pool di risorse introdotto in SQL Server 2016, per gestire il runtime di R e altri processi esterni al motore di database. E può essere utilizzato per monitorare i processi di Python a partire da SQL Server 2017.

Esistono tre tipi di pool di risorse predefiniti:

+ Il *pool interno* rappresenta le risorse usate da SQL Server e non può essere modificato o limitato.
+ Il *pool predefinito* è un pool di utenti predefinito che è possibile usare per modificare l'uso delle risorse per il server nel complesso. È anche possibile definire gruppi di utenti che appartengono al pool, per gestire l'accesso alle risorse.
+ Il *pool esterno predefinito* è un pool di utenti predefinito per le risorse esterne. È anche possibile creare un nuovo pool di risorse esterne e definire i gruppi di utenti che appartengono a questo pool.

Inoltre, è possibile creare *pool di risorse definiti dall'utente* per allocare le risorse al motore di database o ad altre applicazioni e creare *pool di risorse esterne definiti dall'utente* per gestire R e altri processi esterni.

Per una buona introduzione ai concetti generali e alla terminologia, vedere [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md).

## <a name="resource-management-using-resource-governor"></a>Gestione delle risorse con Resource Governor

Se non si conosce Resource Governor, vedere questo argomento per una rapida procedura dettagliata su come modificare le risorse predefinite dell'istanza e creare un nuovo pool di risorse esterne: [Procedura: Creare un pool di risorse per R](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)

È possibile utilizzare il *pool di risorse esterne* meccanismo per gestire le risorse usate da file eseguibili supportati seguenti:

+ Python35.exe quando chiamato da SQL Server o una chiamata in modalità remota con SQL Server come contesto di calcolo remoto
+ BxlServer.exe e processi satellite
+ Avvio avviato dalla finestra di avvio, ad esempio PythonLauncher.dll

> [!NOTE]
> Non è supportata la gestione diretta del servizio Launchpad tramite Resource Governor. Ciò accade perché [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] è un servizio attendibile che da progettazione può ospitare solo utilità di avvio fornite da Microsoft. Le utilità di avvio attendibili sono inoltre configurate per evitare l'utilizzo eccessivo di risorse.

È consigliabile gestire i processi satellite tramite Resource Governor e ottimizzarli in modo da soddisfare le esigenze del carico di lavoro e della configurazione del database specifico.  Qualsiasi processo satellite, ad esempio, può essere creato o eliminato definitivamente on demand durante l'esecuzione.

## <a name="disable-or-enable-external-script-execution"></a>Disabilitare o abilitare l'esecuzione dello Script esterno

Supporto per gli script esterni è facoltativo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del programma di installazione e anche dopo l'installazione è l'esecuzione dello script esterno, completo è impostata su OFF per impostazione predefinita per motivi di sicurezza. Dopo aver completato l'installazione di uno di machine learning lingue e i servizi correlati, pertanto, è necessario riconfigurare in modo esplicito l'istanza e quindi riavviare il servizio motore di database.

In caso di script per tale tipo, è possibile disabilitare tutti l'esecuzione dello script. Sufficiente annullare il processo e impostare la proprietà `external scripts enabled` su FALSE o 0, nell'istanza. Questo modo verrà disabilitato immediatamente qualsiasi esecuzione dello script esterno. È necessario riservare questa opzione per i problemi di sicurezza o situazioni in cui un amministratore deve risolvere immediatamente problemi relativi alle risorse.

## <a name="see-also"></a>Vedere anche

[Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)

