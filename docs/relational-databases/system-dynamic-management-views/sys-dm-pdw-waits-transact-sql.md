---
title: sys.dm_pdw_waits (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.component: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5130e498-1c77-4ae3-a80b-9aae396494e9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 217d79e5730a58ce8c50ccc894e36650d7d32756
ms.sourcegitcommit: abd71294ebc39695d403e341c4f77829cb4166a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36848769"
---
# <a name="sysdmpdwwaits-transact-sql"></a>sys.dm_pdw_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutti i stati rilevati durante l'esecuzione di una richiesta di attesa o query, inclusi i blocchi in attesa in code di trasmissione e così via.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Id numerico univoco associato allo stato di attesa.<br /><br /> Chiave per questa visualizzazione.|Deve essere univoco tra tutte le attese del sistema.|  
|session_id|**nvarchar(32)**|ID della sessione in cui si è verificato lo stato di attesa.|Vedere ID_sessione [DM pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Tipo|**nvarchar(255)**|Tipo di attesa che questa voce rappresenta.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_type|**nvarchar(255)**|Tipo di oggetto interessato dell'attesa.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|object_name|**nvarchar(386)**|Nome o GUID dell'oggetto specificato che è stata interessata dall'attesa.||  
|request_id|**nvarchar(32)**|ID della richiesta in cui si è verificato lo stato di attesa.|Vedere in request_id [DM pdw_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|request_time|**datetime**|Ora in cui è stato richiesto lo stato di attesa.||  
|acquire_time|**datetime**|Ora in cui è stata acquisita il blocco o risorsa.||  
|state|**nvarchar(50)**|Stato di stato di attesa.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Priorità dell'elemento in attesa.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)   
 [sys.dm_pdw_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-wait-stats-transact-sql.md)  
  
  
