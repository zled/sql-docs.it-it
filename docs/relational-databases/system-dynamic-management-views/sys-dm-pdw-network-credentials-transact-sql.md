---
title: sys.dm_pdw_network_credentials (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e7b4534410eabf1186b115c07fef8a8d79960938
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38005783"
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>sys.dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Restituisce un elenco di tutte le credenziali di rete archiviato nel [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] appliance per tutti i server di destinazione. I risultati sono elencati per il nodo di controllo e ogni nodo di calcolo.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Id numerico univoco associato al nodo.|  
|target_server_name|**nvarchar(32)**|Indirizzo IP del server di destinazione che [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] accederà usando le credenziali nome utente e password.|  
|username|**nvarchar(32)**|Nome utente per cui la password viene archiviata.|  
|LAST_MODIFIED|**datetime**|Data e ora dell'ultima operazione che modifica le credenziali.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede VIEW SERVER STATE.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 È la chiave per questa vista a gestione dinamica *pdw_node_id* plus *target_server_name*.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
