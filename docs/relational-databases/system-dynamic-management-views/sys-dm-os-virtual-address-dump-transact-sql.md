---
title: sys.dm_os_virtual_address_dump (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_virtual_address_dump
- sys.dm_os_virtual_address_dump_TSQL
- sys.dm_os_virtual_address_dump
- dm_os_virtual_address_dump_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_virtual_address_dump dynamic management view
ms.assetid: 7b24ea55-3873-42fd-a86c-441c92eb6175
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 451cc209f36a16341cb76ec6ae9319473480d541
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmosvirtualaddressdump-transact-sql"></a>sys.dm_os_virtual_address_dump (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Restituisce informazioni su un intervallo di pagine nello spazio degli indirizzi virtuali del processo chiamante.  
  
> [!NOTE]  
>  Da queste informazioni viene inoltre restituite il **VirtualQuery** API Windows.  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_virtual_address_dump**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**region_base_address**|**varbinary(8)**|Puntatore all'indirizzo di base dell'area delle pagine. Non ammette i valori Null.|  
|**region_allocation_base_address**|**varbinary(8)**|Puntatore all'indirizzo di base di un intervallo di pagine allocate dalla funzione API Windows VirtualAlloc. La pagina a cui punta il membro BaseAddress è inclusa in questo intervallo di allocazione. Non ammette i valori Null.|  
|**region_allocation_protection**|**varbinary(8)**|Attributi di protezione quando l'area è stata allocata per la prima volta. I possibili valori sono i seguenti:<br /><br /> -   PAGE_READONLY<br />-   PAGE_READWRITE<br />-PAGE_NOACCESS<br />-   PAGE_WRITECOPY<br />-   PAGE_EXECUTE<br />-   PAGE_EXECUTE_READ<br />-   PAGE_EXECUTE_READWRITE<br />-   PAGE_EXECUTE_WRITECOPY<br />-PAGE_GUARD<br />-PAGE_NOCACHE<br /><br /> Non ammette i valori Null.|  
|**region_size_in_bytes**|**bigint**|Dimensioni dell'area, in byte, a partire dall'indirizzo di base in cui tutte le pagine hanno gli stessi attributi. Non ammette i valori Null.|  
|**region_state**|**varbinary(8)**|Stato corrente dell'area. I possibili valori sono i seguenti:<br /><br /> -   MEM_COMMIT<br />-   MEM_RESERVE<br />-   MEM_FREE<br /><br /> Non ammette i valori Null.|  
|**region_current_protection**|**varbinary(8)**|Attributi di protezione. I possibili valori sono i seguenti:<br /><br /> -   PAGE_READONLY<br />-   PAGE_READWRITE<br />-PAGE_NOACCESS<br />-   PAGE_WRITECOPY<br />-   PAGE_EXECUTE<br />-   PAGE_EXECUTE_READ<br />-   PAGE_EXECUTE_READWRITE<br />-   PAGE_EXECUTE_WRITECOPY<br />-PAGE_GUARD<br />-PAGE_NOCACHE<br /><br /> Non ammette i valori Null.|  
|**region_type**|**varbinary(8)**|Identifica i tipi di pagine nell'area. I possibili valori sono i seguenti:<br /><br /> -   MEM_PRIVATE<br />-   MEM_MAPPED<br />-   MEM_IMAGE<br /><br /> Non ammette i valori Null.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Relative al sistema operativo SQL Server viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


