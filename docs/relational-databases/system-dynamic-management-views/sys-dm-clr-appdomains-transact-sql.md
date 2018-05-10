---
title: sys.dm_clr_appdomains (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_clr_appdomains
- sys.dm_clr_appdomains
- dm_clr_appdomains_TSQL
- sys.dm_clr_appdomains_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_appdomains dynamic management dynamic management view
ms.assetid: 9fe0d4fd-950a-4274-a493-85e776278045
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 501e126a3064489852987671c83326f0d4a53832
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmclrappdomains-transact-sql"></a>sys.dm_clr_appdomains (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni dominio dell'applicazione nel server. Dominio dell'applicazione (**AppDomain**) è un costrutto di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR) che è l'unità di isolamento per un'applicazione. È possibile utilizzare questa visualizzazione per comprendere e risolvere i problemi relativi a oggetti dell'integrazione con CLR che sono in esecuzione in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Esistono diversi tipi di oggetti di database gestito dell'integrazione con CLR. Per informazioni generali su questi oggetti, vedere [compilazione di oggetti di Database con l'integrazione di Common Language Runtime (CLR)](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md). Ogni volta che questi oggetti vengono eseguiti, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crea un **AppDomain** in cui viene caricato ed eseguito il codice necessario. Il livello di isolamento per un **AppDomain** uno **AppDomain** per database per proprietario. Vale a dire tutti gli oggetti CLR di proprietà di un utente vengono sempre eseguiti nello stesso **AppDomain** per database (se un utente registra oggetti di database CLR in database diversi, il database CLR gli oggetti verranno eseguiti in domini applicazione diversi). Un **AppDomain** non viene eliminato al termine dell'esecuzione di codice. ma viene memorizzato nella cache per le future esecuzioni. Ciò migliora le prestazioni.  
  
 Per ulteriori informazioni, vedere [domini applicazione](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**appdomain_address**|**varbinary(8)**|Indirizzo del **AppDomain**. Database gestito tutti gli oggetti appartenenti a un utente vengono sempre caricati nello stesso **AppDomain**. È possibile utilizzare questa colonna per cercare tutti gli assembly attualmente caricati in questo **AppDomain** in **Sys.dm clr_loaded_assemblies**.|  
|**appdomain_id**|**int**|ID di **AppDomain**. Ogni **AppDomain** ha un ID univoco.|  
|**appdomain_name**|**varchar(386)**|Nome di **AppDomain** assegnato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**creation_time**|**datetime**|Ora in cui il **AppDomain** è stato creato. Poiché **AppDomain** vengono memorizzati nella cache e riutilizzati per migliorare le prestazioni, **creation_time** non è necessariamente l'esecuzione quando il codice.|  
|**db_id**|**int**|ID del database in cui il **AppDomain** è stato creato. Codice archiviato in due database diversi non può condividere un **AppDomain**.|  
|**user_id**|**int**|ID dell'utente i cui oggetti possono essere eseguiti in questa **AppDomain**.|  
|**state**|**nvarchar(128)**|Un descrittore per lo stato corrente del **AppDomain**. Un AppDomain può trovarsi in stati diversi dalla creazione all'eliminazione. Per ulteriori informazioni, vedere la sezione Osservazioni di questo argomento.|  
|**strong_refcount**|**int**|Numero di riferimenti forti al **AppDomain**. Ciò riflette il numero di batch in esecuzione che utilizzano questo **AppDomain**. Si noti che l'esecuzione di questa vista verrà creato un **strong refcount**; anche se nessun codice attualmente in esecuzione, **strong_refcount** avrà un valore pari a 1.|  
|**weak_refcount**|**int**|Numero di riferimenti deboli al **AppDomain**. Indica il numero di oggetti di **AppDomain** vengono memorizzati nella cache. Quando si esegue un oggetto di database gestito, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memorizza nella cache all'interno di **AppDomain** per il riutilizzo futuro. Ciò migliora le prestazioni.|  
|**cost**|**int**|Costo del **AppDomain**. Maggiore è il costo, più è probabile che questo **AppDomain** debba essere scaricato eccessivo della memoria. Costo dipende in genere la quantità di memoria è necessario ricreare questo **AppDomain**.|  
|**Valore**|**int**|Valore di **AppDomain**. Minore è il valore, più è probabile che questo **AppDomain** debba essere scaricato eccessivo della memoria. Valore dipende in genere che utilizzano il numero di connessioni o batch **AppDomain**.|  
|**total_processor_time_ms**|**bigint**|Tempo totale del processore, in millisecondi, utilizzato da tutti i thread durante l'esecuzione nel dominio dell'applicazione corrente dall'avvio del processo. Ciò equivale a **System.AppDomain.MonitoringTotalProcessorTime**.|  
|**total_allocated_memory_kb**|**bigint**|Dimensioni totali, in kilobyte, di tutte le allocazioni di memoria eseguite dal dominio dell'applicazione dalla sua creazione, senza sottrarre la memoria raccolta. Ciò equivale a **System.AppDomain.MonitoringTotalAllocatedMemorySize**.|  
|**survived_memory_kb**|**bigint**|Numero di kilobyte rimanenti dall'ultima raccolta di blocco completa e a cui fa riferimento il dominio dell'applicazione corrente. Ciò equivale a **System.AppDomain.MonitoringSurvivedMemorySize**.|  
  
## <a name="remarks"></a>Osservazioni  
 È una relazione uno-a-molti tra **dm_clr_appdomains** e **dm_clr_loaded_assemblies**.  
  
 Nelle tabelle seguenti sono elencati i possibili **stato** valori, le relative descrizioni, e quando si verificano nel **AppDomain** ciclo di vita. È possibile utilizzare queste informazioni per seguire il ciclo di vita di un **AppDomain** e guardare un video sospette o ripetitive **AppDomain** senza la necessità di analizzare il registro eventi di Windows lo scaricamento di istanze.  
  
## <a name="appdomain-initialization"></a>Inizializzazione di AppDomain  
  
|State|Description|  
|-----------|-----------------|  
|E_APPDOMAIN_CREATING|Il **AppDomain** viene creato.|  
  
## <a name="appdomain-usage"></a>Utilizzo di AppDomain  
  
|State|Description|  
|-----------|-----------------|  
|E_APPDOMAIN_SHARED|Il runtime **AppDomain** è pronto per essere utilizzato da più utenti.|  
|E_APPDOMAIN_SINGLEUSER|Il **AppDomain** è pronto per l'utilizzo nelle operazioni DDL. Queste ultime differiscono da E_APPDOMAIN_SHARED per il fatto che gli AppDomain condivisi vengono utilizzati per le esecuzioni di integrazione di CLR e non per operazioni DDL. Tali AppDomain sono isolati da altre operazioni simultanee.|  
|E_APPDOMAIN_DOOMED|Il **AppDomain** è pianificata per essere scaricato, ma sono attualmente presenti thread in esecuzione in essa contenuti.|  
  
## <a name="appdomain-cleanup"></a>Eliminazione di AppDomain  
  
|State|Description|  
|-----------|-----------------|  
|E_APPDOMAIN_UNLOADING|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha richiesto che CLR scarichi il **AppDomain**, in genere perché l'assembly che contiene gli oggetti di database gestiti è stato modificato o eliminato.|  
|E_APPDOMAIN_UNLOADED|Il CLR ha scaricato la **AppDomain**. Si tratta in genere il risultato di una procedura di escalation a causa di **ThreadAbort**, **OutOfMemory**, o un'eccezione non gestita nel codice utente.|  
|E_APPDOMAIN_ENQUEUE_DESTROY|Il **AppDomain** è stato scaricato in CLR e impostato per l'eliminazione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|E_APPDOMAIN_DESTROY|Il **AppDomain** è in corso l'eliminazione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|E_APPDOMAIN_ZOMBIE|Il **AppDomain** è stato eliminato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; tuttavia, non tutti i riferimenti di **AppDomain** sono stati puliti.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE nel database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come visualizzare i dettagli di un **AppDomain** per un determinato assembly:  
  
```  
select appdomain_id, creation_time, db_id, user_id, state  
from sys.dm_clr_appdomains a  
where appdomain_address =   
(select appdomain_address   
 from sys.dm_clr_loaded_assemblies  
   where assembly_id = 500);  
```  
  
 Nell'esempio seguente viene illustrato come visualizzare tutti gli assembly in un determinato **AppDomain**:  
  
```  
select a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
from sys.dm_clr_loaded_assemblies as l   
inner join sys.assemblies as a  
on l.assembly_id = a.assembly_id  
where l.appdomain_address =   
(select appdomain_address   
from sys.dm_clr_appdomains  
where appdomain_id = 15);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_clr_loaded_assemblies &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)   
 [Viste a gestione dinamica relative a Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
