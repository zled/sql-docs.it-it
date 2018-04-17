---
title: Sys.dm_pdw_resource_waits (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.service: sql-data-warehouse
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a43ce9a2-5261-41e3-97f0-555ba05ebed9
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 5a5d4fc8a93df931028bca874ae12fd0980758be
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwresourcewaits-transact-sql"></a>sys.dm_pdw_resource_waits (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Consente di visualizzare informazioni per tutti i tipi di risorsa in attesa [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|Posizione della richiesta nella lista di attesa.|ordinale in base 0. Questo non è univoco tra tutte le voci di attesa.|  
|session_id|**nvarchar(32)**|ID della sessione in cui si è verificato lo stato di attesa.|Vedere session_id in [sys.dm_pdw_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|Tipo|**nvarchar(255)**|Tipo di attesa che rappresenta questa voce.|I valori possibili sono:<br /><br /> Connessione<br /><br /> Concorrenza di query locale<br /><br /> Concorrenza di query distribuite<br /><br /> Concorrenza DMS<br /><br /> Concorrenza di backup|  
|object_type|**nvarchar(255)**|Tipo di oggetto interessato dall'attesa.|I valori possibili sono:<br /><br /> **OBJECT**<br /><br /> **DATABASE**<br /><br /> **SYSTEM**<br /><br /> **SCHEMA**<br /><br /> **APPLICAZIONE**|  
|object_name|**nvarchar(386)**|Nome o il GUID dell'oggetto specificato a cui si è verificato per l'attesa.|Tabelle e viste vengono visualizzate con nomi in tre parti.<br /><br /> Gli indici e le statistiche vengono visualizzate con nomi in quattro parti.<br /><br /> I nomi di entità e i database sono nomi di stringa.|  
|request_id|**nvarchar(32)**|ID della richiesta in cui si è verificato lo stato di attesa.|Identificatore QID della richiesta.<br /><br /> Identificatore GUID per le richieste di carico.|  
|request_time|**datetime**|Ora in cui è stato richiesto il blocco o la risorsa.||  
|acquire_time|**datetime**|Ora in cui è stato acquisito il blocco o la risorsa.||  
|state|**nvarchar(50)**|Stato di stato di attesa.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|Priorità dell'attesa.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|concurrency_slots_used|**int**|Numero di slot della concorrenza (numero massimo di 32) sono riservato per la richiesta.|1 – per SmallRC<br /><br /> 3 – per MediumRC<br /><br /> 7 per LargeRC<br /><br /> 22: per XLargeRC|  
|resource_class|**nvarchar(20)**|Classe di risorse per questa richiesta.|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
