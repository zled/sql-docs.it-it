---
title: "Procedura: Creare un Pool di risorse per R | Microsoft Docs"
ms.custom: ""
ms.date: "10/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7f7f6e4-774d-4b45-b94a-f06c51718475
caps.latest.revision: 19
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 19
---
# Procedura: Creare un Pool di risorse per R
  Questo argomento viene descritto come creare un pool di risorse in modo specifico per la gestione dei carichi di lavoro R in [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Presuppone che sia già stato installato Servizi di R (Database) e riconfigurare il [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] istanza per supportare più granulari per le gestione delle risorse utilizzate da R.  
  
 Per ulteriori informazioni sulla gestione delle risorse di server, vedere [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) e [Resource Governor correlati viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md).  
  
 **Passaggi**  
  
1.  Controllare lo stato del pool di risorse esistente  
  
2.  Modificare il pool di risorse server  
  
3.  Creare un nuovo pool di risorse per i processi esterni  
  
4.  Creare una funzione di classificazione per identificare le richieste di R  
  
5.  Verificare che i processi R è acquisizione di nuovo pool di risorse esterne  
  
##  <a name="bkmk_ReviewStatus"></a> Verificare lo stato del pool di risorse esistente  
  
1.  Innanzitutto, controllare le risorse allocate al pool predefinito per il server.  
  
    ```  
    SELECT * FROM sys.resource_governor_resource_pools WHERE name = 'default'  
    ```  
     **Risultati**

    |pool_id|name|min_cpu_percent|max_cpu_percent|min_memory_percent|max_memory_percent|cap_cpu_percent|min_iops_per_volume|max_iops_per_volume|  
    |-|-|-|-|-|-|-|-|-|  
    |2|predefiniti|0|100|0|100|100|0|0|  

2.  Controllare le risorse allocate per il valore predefinito **esterno** pool di risorse.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools WHERE name = 'default'  
    ```  
     
    **Risultati**

    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|predefiniti|100|20|0|2|  
 
3.  In queste impostazioni predefinite del server, il runtime R avrà probabilmente risorse insufficienti per completare la maggior parte delle attività. Per modificare questa impostazione, è necessario modificare l'utilizzo delle risorse di server come indicato di seguito:  
  
    -   Ridurre la memoria massima che può essere utilizzata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
    -   aumentare la memoria massima che può essere utilizzata per il processo esterno  
  
## Modificare l'utilizzo delle risorse server  
  
1.  In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], eseguire l'istruzione seguente per limitare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzo di memoria di **il 60%** del valore nell'impostazione di 'max server memory'.  
  
    ```  
    ALTER RESOURCE POOL "default" WITH (max_memory_percent = 60);  
    ```  
  
2.  Analogamente, eseguire l'istruzione seguente per limitare l'uso della memoria da processi esterni a **40%** delle risorse totali del computer.  
  
    ```  
    ALTER EXTERNAL RESOURCE POOL "default" WITH (max_memory_percent = 40);  
    ```  
  
3.  Per applicare queste modifiche, è necessario riconfigurare e riavviare Resource Governor come indicato di seguito:  
  
    ```  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
    > [!NOTE]  
    >  Si tratta di impostazioni appena suggerite per iniziare. è necessario valutare i requisiti di R con altri processi del server per determinare il giusto equilibrio per l'ambiente e il carico di lavoro.  
  
## Creare un pool di risorse esterne definite dall'utente  
  
1.  Tutte le modifiche alla configurazione di Resource Governor vengono applicate a livello di server nel suo complesso e influiscono su carichi di lavoro che utilizzano il pool predefinito per il server, nonché i carichi di lavoro che utilizzano il pool esterno.  
  
     Pertanto, per fornire un controllo più preciso in cui i carichi di lavoro deve avere la precedenza, è possibile creare un nuovo pool di risorse esterne definite dall'utente. Deve inoltre definire una funzione di classificazione e assegnarlo al pool di risorse esterno.  
  
     Iniziare creando un nuovo *pool di risorse esterne definite dall'utente*. Nell'esempio seguente, il pool è denominato **ds_ep**.  
  
    ```  
    CREATE EXTERNAL RESOURCE POOL ds_ep WITH (max_memory_percent = 40);  
    ```  
  
     Si noti il nuovo **ESTERNO** (parola chiave).  
  
2.  Creare un gruppo di carico di lavoro denominato `ds_wg` per gestire le richieste di sessione. Per le query SQL verrà utilizzato il pool predefinito; per tutti i processi esterni query utilizzerà il `ds_ep` pool.  
  
    ```  
    CREATE WORKLOAD GROUP ds_wg WITH (importance = medium) USING "default", EXTERNAL "ds_ep";  
    ```  
  
     Le richieste vengono assegnate al gruppo predefinito ogni volta che la richiesta non può essere classificata, o se è presente qualsiasi altro errore di classificazione.  
  
     Per ulteriori informazioni, vedere [gruppo del carico di lavoro di Resource Governor](../../relational-databases/resource-governor/resource-governor-workload-group.md) e [CREATE WORKLOAD GROUP &#40; Transact-SQL &#41;](../../t-sql/statements/create-workload-group-transact-sql.md).  
  
## Creare una funzione di classificazione per R  
  
1.  Una funzione di classificazione vengono esaminate le attività in ingresso e determina se l'attività è quello che può essere eseguito utilizzando il pool di risorse corrente. Attività che non soddisfano i criteri della funzione di classificazione vengono assegnate al pool di risorse predefinito del server.  
  
     Per iniziare è necessario specificare che una funzione di classificazione deve essere utilizzata da Resource Governor per determinare i pool di risorse. È possibile assegnare un valore null come segnaposto per la funzione di classificazione.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH (classifier_function = NULL);  
    ALTER RESOURCE GOVERNOR reconfigure;  
    ```  
  
     Per altre informazioni, vedere [ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md).  
  
2.  Nella funzione di classificazione per ogni pool di risorse, definire il tipo di istruzioni o le richieste in ingresso che devono essere assegnate al pool di risorse.  
  
     Ad esempio, la funzione seguente restituisce il nome dello schema assegnato al pool di risorse esterne definite dall'utente se l'applicazione che ha inviato la richiesta è 'Microsoft R Host' o 'RStudio'; in caso contrario restituirà il pool di risorse predefinito.  
  
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
  
3.  Quando la funzione è stata creata, riconfigurare il gruppo di risorse per assegnare la nuova funzione di classificazione per il gruppo di risorse esterni definiti in precedenza.  
  
    ```  
    ALTER RESOURCE GOVERNOR WITH  (classifier_function = dbo.is_ds_apps);  
    ALTER RESOURCE GOVERNOR WITH reconfigure;  
    go  
    ```  
  
## Verificare l'affinità e nuovo pool di risorse  
  
1.  Per verificare che le modifiche sono state apportate, controllare la configurazione di memoria del server e della CPU per ognuno dei gruppi del carico di lavoro associati a tutti i pool di risorse di istanza: il pool predefinito per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server e pool di risorse predefinito per i processi esterni al pool definiti dall'utente per processi esterni.  
  
    ```  
    SELECT * FROM sys.resource_governor_workload_groups;  
    ```  

    **Risultati**

    |group_id|name|importance|request_max_memory_grant_percent|request_max_cpu_time_sec|request_memory_grant_timeout_sec|max_dop|GROUP_MAX_REQUESTS pool_id|pool_idd|external_pool_idd|  
    |-|-|-|-|-|-|-|-|-|-|  
    |1|interno|Media|25|0|0|0|0|1|2|  
    |2|predefiniti|Media|25|0|0|0|0|2|2|  
    |256|ds_wg|Media|25|0|0|0|0|2|256|  
  
2.  È possibile utilizzare la nuova vista del catalogo, [sys.resource_governor_external_resource_pools &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), per visualizzare tutti i pool di risorse esterno.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pools;  
    ```  
    **Risultati**
    
    |external_pool_id|name|max_cpu_percent|max_memory_percent|max_processes|version|  
    |-|-|-|-|-|-|  
    |2|predefiniti|100|20|0|2|  
    |256|ds_ep|100|40|0|1|  
  
     Per ulteriori informazioni, vedere [viste del catalogo di Resource Governor &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md).  
  
3.  L'istruzione seguente restituisce informazioni sulle risorse del computer che viene creata un'affinità al pool di risorse esterno.  
  
    ```  
    SELECT * FROM sys.resource_governor_external_resource_pool_affinity;  
    ```  
  
     In questo caso, poiché i pool sono stati creati con un'affinità di AUTO, non viene visualizzata alcuna informazione. Per ulteriori informazioni, vedere [sys.dm_resource_governor_resource_pool_affinity &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md).  
  
## Vedere anche  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Governance delle risorse per i servizi di R](../../advanced-analytics/r-services/resource-governance-for-r-services.md)  
  
  