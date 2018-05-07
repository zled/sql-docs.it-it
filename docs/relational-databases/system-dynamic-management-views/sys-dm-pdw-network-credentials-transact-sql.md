---
title: sys.dm_pdw_network_credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.component: dmv's
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 511474f73a6bc6c1a1f2310a4fa2615f43847e77
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>sys.dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Restituisce un elenco di tutte le credenziali di rete archiviato nel [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] dispositivo per tutti i server di destinazione. Per il nodo di controllo e ogni nodo di calcolo sono elencati i risultati.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Id numerico univoco associato al nodo.|  
|target_server_name|**nvarchar(32)**|Indirizzo IP del server di destinazione che [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] accederà utilizzando le credenziali di nome utente e password.|  
|username|**nvarchar(32)**|Nome utente per cui la password viene archiviata.|  
|LAST_MODIFIED|**datetime**|Data e ora dell'ultima operazione che modifica le credenziali.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede VIEW SERVER STATE.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 La chiave per questa vista a gestione dinamica è *pdw_node_id* più *target_server_name*.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
