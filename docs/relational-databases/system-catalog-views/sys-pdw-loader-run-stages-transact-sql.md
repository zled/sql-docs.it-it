---
title: sys.pdw_loader_run_stages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: pdw
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 255681e9-323c-42c0-a63c-1f05536efdd5
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 47f178b3dc975477bfbdadc1fee3dcfbf7ee3001
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="syspdwloaderrunstages-transact-sql"></a>sys.pdw_loader_run_stages (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Contiene informazioni sulle operazioni di caricamento in corso e completate in [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]. Le informazioni vengono mantenute tra un riavvio di sistema e l'altro.  
  
|||||  
|-|-|-|-|  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|run_id|**int**|Identificatore univoco di un caricatore di esecuzione.||  
|fase|**nvarchar(30)**|La fase corrente per l'esecuzione.|'CREATE_STAGING', 'DMS_LOAD', 'LOAD_INSERT', 'LOAD_CLEANUP'|  
|request_id|**nvarchar(32)**|ID della richiesta in questa fase di esecuzione.||  
|status|**nvarchar (16)**|Stato di questa fase.||  
|start_time|**datetime**|Ora di inizio della fase.||  
|end_time|**datetime**|Ora di fine della fase, se presente.|NULL se non è avviato o è in corso.|  
|total_elapsed_time|**int**|Tempo totale di questa fase dedicato (o finora trascorso) in esecuzione.|Se total_elapsed_time supera il valore massimo per un numero intero (24.8 giorni, in millisecondi), errore di materializzazione scadenza comporterà un overflow.<br /><br /> Il valore massimo in millisecondi è equivalente a 24.8 giorni.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste del catalogo Parallel Data Warehouse](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
