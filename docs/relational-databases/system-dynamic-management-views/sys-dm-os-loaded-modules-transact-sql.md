---
title: Sys.dm os_loaded_modules (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_loaded_modules
- dm_os_loaded_modules
- sys.dm_os_loaded_modules_TSQL
- dm_os_loaded_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_loaded_modules dynamic management view
ms.assetid: 56c7743a-b568-4943-bd3b-73c57d9d641c
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c84cab897864acf1b6d77f847b08a0c06e46a157
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmosloadedmodules-transact-sql"></a>sys.dm_os_loaded_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni modulo caricato nello spazio degli indirizzi del server.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_loaded_modules**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**base_address**|**varbinary(8)**|Indirizzo del modulo nel processo.|  
|**file_version**|**varchar(23)**|Versione del file visualizzata nel formato seguente:<br /><br /> x.x:x.x|  
|**product_version**|**varchar(23)**|Versione del prodotto visualizzata nel formato seguente:<br /><br /> x.x:x.x|  
|**debug**|**bit**|1 = Il modulo è una versione debug del modulo caricato.|  
|**patched**|**bit**|1 = Al modulo sono state applicate patch.|  
|**versione provvisoria**|**bit**|1 = Il modulo è una versione non finale del modulo caricato.|  
|**private_build**|**bit**|1 = Il modulo è una build privata del modulo caricato.|  
|**special_build**|**bit**|1 = Il modulo è una build speciale del modulo caricato.|  
|**Lingua**|**int**|Lingua delle informazioni sulla versione del modulo.|  
|**Società**|**nvarchar(256)**|Nome della società che ha creato il modulo.|  
|**description**|**nvarchar(256)**|Descrizione del modulo.|  
|**name**|**nvarchar(255)**|Nome del modulo. Include il percorso completo del modulo.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative al sistema di operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  
