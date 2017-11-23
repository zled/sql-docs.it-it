---
title: Sys.dm os_loaded_modules (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
caps.latest.revision: "20"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3c260b70aca72d90254571bc819dd20704bafbb0
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni modulo caricato nello spazio degli indirizzi del server.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_loaded_modules**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary (8)**|Indirizzo del modulo nel processo.|  
|**file_version**|**varchar(23)**|Versione del file visualizzata nel formato seguente:<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|Versione del prodotto visualizzata nel formato seguente:<br /><br /> x.x:x.x|  
|**eseguire il debug**|**bit**|1 = Il modulo è una versione debug del modulo caricato.|  
|**patch**|**bit**|1 = Al modulo sono state applicate patch.|  
|**versione provvisoria**|**bit**|1 = Il modulo è una versione non finale del modulo caricato.|  
|**private_build**|**bit**|1 = Il modulo è una build privata del modulo caricato.|  
|**special_build**|**bit**|1 = Il modulo è una build speciale del modulo caricato.|  
|**lingua**|**int**|Lingua delle informazioni sulla versione del modulo.|  
|**società**|**nvarchar(256)**|Nome della società che ha creato il modulo.|  
|**Descrizione**|**nvarchar(256)**|Descrizione del modulo.|  
|**name**|**nvarchar(255)**|Nome del modulo. Include il percorso completo del modulo.|  
|**pdw_node_id**|**int**|**Si applica a**:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Relative al sistema operativo SQL Server viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
