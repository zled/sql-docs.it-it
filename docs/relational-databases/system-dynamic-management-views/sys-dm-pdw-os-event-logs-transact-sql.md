---
title: sys.dm_pdw_os_event_logs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.service: ''
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: a0daa8cf-72e2-4349-8be1-d3cc0f9b1e02
caps.latest.revision: 7
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c341882b510f5a602f7c534ca653208b1784b426
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmpdwoseventlogs-transact-sql"></a>sys.dm_pdw_os_event_logs (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contiene informazioni sull'evento di Windows diverse registra in nodi diversi.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|pdw_node_id|**int**|Nodo dispositivo che si trova in questo log.<br /><br /> pdw_node_id e nome_registro formano la chiave per la visualizzazione.||  
|log_name|**nvarchar(255)**|Nome registro eventi di Windows.<br /><br /> pdw_node_id e nome_registro formano la chiave per la visualizzazione.||  
|log_source|**nvarchar(255)**|Nome di origine del registro eventi di Windows.||  
|event_id|**int**|ID dell'evento. Non è univoco.||  
|event_type|**nvarchar(255)**|Tipo di evento, che identifica la gravità.|'Informazioni', 'Avviso', 'Error'|  
|event_message|**nvarchar(4000)**|Dettagli dell'evento.||  
|generate_time|**datetime**|Ora di che creazione dell'evento.||  
|write_time|**datetime**|Ora che dell'evento è stato effettivamente scritti nel log.||  
  
 Per informazioni sulle righe massimi mantenuto da questa vista, vedere la sezione valori massimi vista di sistema nel [valori minimo e massimo (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9) argomento.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
