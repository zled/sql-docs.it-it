---
title: 'Procedura: Creare un pool di risorse per R | Microsoft Docs'
ms.custom: 
ms.date: 10/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: be3afb3a1ff5175fbb3d0735cde59bd19bb47f6c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="how-to-create-a-resource-pool-for-r"></a>Procedura: Creare un pool di risorse per R
  Questo argomento descrive come creare un pool di risorse specifico per la gestione di carichi di lavoro R in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Si presuppone che sia stato già installato R Services (In-Database) e che si voglia riconfigurare l'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per supportare una gestione con granularità più fine delle risorse usate da R.  
  
 Per altre informazioni sulla gestione delle risorse del server, vedere [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) e [Viste a gestione dinamica relative a Resource Governor (Transact-SQL) &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).  
  
 **Passaggi**  
  
1.  Esaminare lo stato dei pool di risorse esistenti  
  
2.  Modificare i pool di risorse del server  
  
3.  Creare un nuovo pool di risorse per processi esterni  
  
4.  Creare una funzione di classificazione per identificare le richieste R  
  
5.  Verificare che il nuovo pool di risorse esterne acquisisca processi R  
  
##  <a name="bkmk_ReviewStatus"></a> Esaminare lo stato dei pool di risorse esistenti  
  
1.  Prima di tutto, controllare le risorse allocate al pool predefinito per il server.  
  
    ```  
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'  
    ```  
     **Risultati**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|  
    |-|-|-|-|-|-|-|-|-|  
    |2|predefiniti|0|100|0|100|100|0|0|  

2.  Controllare le risorse allocate al pool di risorse **esterno** predefinito.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'  
    ```  
     
    **Risultati**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|predefiniti|100|20|0|2|  
 
3.  In queste impostazioni predefinite del server il runtime R avrà probabilmente risorse insufficienti per completare la maggior parte delle attività. Per ovviare a questa situazione, è necessario modificare l'utilizzo delle risorse del server in questo modo:  
  
    -   Ridurre la memoria massima del computer che può essere usata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
    -   Aumentare la memoria massima del computer che può essere usata dal processo esterno  
  
## <a name="modify-server-resource-usage"></a>Modificare l'utilizzo delle risorse del server  
  
1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] eseguire l'istruzione seguente per limitare l'utilizzo della memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al **60%** del valore specificato nell'impostazione 'max server memory'.  
  
    ```  
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);  
    ```  
  
2.  Analogamente, eseguire l'istruzione seguente per limitare l'uso di memoria da parte dei processi esterni al **40%** delle risorse totali del computer.  
  
    ```  
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);  
    ```  
  
3.  Per applicare queste modifiche, è necessario riconfigurare e riavviare Resource Governor in questo modo:  
  
    ```  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
    > [!NOTE]  
    >  Queste sono solo le impostazioni consigliate da cui iniziare. È bene valutare i requisiti di R rispetto ad altri processi del server per determinare il corretto equilibrio per l'ambiente e il carico di lavoro.  
  
## <a name="create-a-user-defined-external-resource-pool"></a>Creare un pool di risorse esterno definito dall'utente  
  
1.  Qualsiasi modifica apportata alla configurazione di Resource Governor viene applicata al server complessivamente e influisce sui carichi di lavoro che usano i pool predefiniti per il server, nonché su quelli che usano i pool esterni.  
  
     Di conseguenza, per fornire un controllo con granularità più fine sui carichi di lavoro che devono avere la precedenza, è possibile creare un nuovo pool di risorse esterno definito dall'utente. È anche consigliabile definire una funzione di classificazione e assegnarla al pool di risorse esterno.  
  
     Per iniziare, creare un nuovo *pool di risorse esterno definito dall'utente*. Nell'esempio seguente il pool si chiama **ds_ep**.  
  
    ```  
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);  
    ```  
  
     Notare la nuova parola chiave **EXTERNAL**.  
  
2.  Creare un gruppo di carico di lavoro denominato `ds_wg` da usare per la gestione delle richieste di sessione. Per le query SQL verrà usato il pool predefinito, mentre per tutti i processi esterni le query useranno il pool `ds_ep`.  
  
    ```  
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";  
    ```  
  
     Le richieste vengono assegnate al gruppo predefinito ogni volta che la richiesta non può essere classificata o se si è verificato un altro errore di classificazione.  
  
     Per altre informazioni, vedere [Gruppo di carico di lavoro di Resource Governor](../../relational-databases/resource-governor/resource-governor-workload-group.md) e [CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-workload-group-transact-sql.md).  
  
## <a name="create-a-classification-function-for-r"></a>Creare una funzione di classificazione per R  
  
1.  Una funzione di classificazione esamina le attività in ingresso e determina se l'attività possa essere eseguita usando il pool di risorse corrente. Le attività che non soddisfano i criteri della funzione di classificazione vengono riassegnate al pool di risorse predefinito del server.  
  
     Per iniziare, specificare che una funzione di classificazione deve essere usata da Resource Governor per determinare i pool di risorse. È possibile assegnare un valore Null come segnaposto per la funzione di classificazione.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
     Per altre informazioni, vedere [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).  
  
2.  Nella funzione di classificazione per ogni pool di risorse definire il tipo di istruzioni o di richieste in ingresso che devono essere assegnate al pool di risorse.  
  
     Ad esempio, la funzione seguente restituisce il nome dello schema assegnato al pool di risorse esterno definito dall'utente se l'applicazione che ha inviato la richiesta è 'Microsoft R Host' o 'RStudio'. In caso contrario, restituisce il pool di risorse predefinito.  
  
    ```  
    USE master  
    GO  
    CREATE FUNCTION is_ds_apps()  
    RETURNS sysname  
    WITH schemabinding  
    AS  
    BEGIN  
        IF program_name() in ('Microsoft R Host', 'RStudio') RETURN 'ds_wg';  
        RETURN 'default'  
        END;  
    GO  
    ```  
  
3.  Dopo la creazione della funzione, riconfigurare il gruppo di risorse in modo da assegnare la nuova funzione di classificazione al gruppo di risorse esterno definito in precedenza.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);  
    ALTER RESOURCE GOVERNOR WITH reconfigure;  
    go  
    ```  
  
## <a name="verify-new-resource-pools-and-affinity"></a>Verificare i nuovi pool di risorse e l'affinità  
  
1.  Per verificare le modifiche apportate, controllare la configurazione della memoria e della CPU del server per ognuno dei gruppi di carico di lavoro associati a tutti i pool di risorse dell'istanza: il pool predefinito per il server[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il pool di risorse predefinito per processi esterni e il pool definito dall'utente per processi esterni.  
  
    ```  
    SELECT * FROM sys.resource_governor_workload_groups;  
    ```  

    **Risultati**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|group_max_requests pool_id|pool_idd|external_pool_idd|  
    |-|-|-|-|-|-|-|-|-|-|  
    |1|interno|Media|25|0|0|0|0|1|2|  
    |2|predefiniti|Media|25|0|0|0|0|2|2|  
    |256|ds_wg|Media|25|0|0|0|0|2|256|  
  
2.  È possibile usare la nuova vista del catalogo [sys.resource_governor_external_resource_pools &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md) per visualizzare tutti i pool di risorse esterni.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools;  
    ```  
    **Risultati**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|predefiniti|100|20|0|2|  
    |256|ds_ep|100|40|0|1|  
  
     Per altre informazioni, vedere [Viste del catalogo di Resource Governor &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).  
  
3.  L'istruzione seguente restituisce informazioni sulle risorse del computer per le quali è impostata l'affinità al pool di risorse esterno.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;  
    ```  
  
     In questo caso, poiché i pool sono stati creati con affinità AUTO, non viene visualizzata alcuna informazione. Per altre informazioni, vedere [sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Governance delle risorse per R Services](../../advanced-analytics/r-services/resource-governance-for-r-services.md)  
  
  

