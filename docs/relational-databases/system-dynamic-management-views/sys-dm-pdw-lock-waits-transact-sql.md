---
title: sys.dm_pdw_lock_waits (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8ef966f8-d14e-40d3-9626-3508ada9b8fb
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: b5653fbf12b95f36e23ffe8c0855c6da247ecd37
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwlockwaits-transact-sql"></a>sys.dm_pdw_lock_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni sulle richieste in attesa di blocchi.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Posizione della richiesta nella lista di attesa.|ordinale in base 0. Questo non è univoco tra tutte le voci di attesa.|  
|session_id|**nvarchar(32)**|ID della sessione in cui si è verificato lo stato di attesa.|Vedere session_id in [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Tipo|**nvarchar(255)**|Tipo di attesa che rappresenta questa voce.|I valori possibili sono:<br /><br /> Origine dati<br /><br /> SharedUpdate<br /><br /> ExclusiveUpdate<br /><br /> Exclusive|  
|object_type|**nvarchar(255)**|Tipo di oggetto interessato dall'attesa.|I valori possibili sono:<br /><br /> OBJECT<br /><br /> DATABASE<br /><br /> SYSTEM<br /><br /> SCHEMA<br /><br /> APPLICATION|  
|object_name|**nvarchar(386)**|Nome o il GUID dell'oggetto specificato a cui si è verificato per l'attesa.|Tabelle e viste vengono visualizzate con nomi in tre parti.<br /><br /> Gli indici e le statistiche vengono visualizzate con nomi in quattro parti.<br /><br /> I nomi di entità e i database sono nomi di stringa.|  
|request_id|**nvarchar(32)**|ID della richiesta in cui si è verificato lo stato di attesa.|ID della richiesta.<br /><br /> Questo è un GUID per le richieste di carico.|  
|request_time|**datetime**|Ora in cui è stato richiesto il blocco o la risorsa.||  
|acquire_time|**datetime**|Ora in cui è stato acquisito il blocco o la risorsa.||  
|state|**nvarchar(50)**|Stato di stato di attesa.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Priorità dell'attesa.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
