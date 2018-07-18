---
title: sys.dm_pdw_exec_sessions (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31c262b3-7e4d-44c4-af71-aaef0fd1a980
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: ce411196b28f658789769cd53aa86693d747ef47
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmpdwexecsessions-transact-sql"></a>sys.dm_pdw_exec_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutte le sessioni attualmente o recentemente aperti nel dispositivo. Contiene una riga per ogni sessione.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|session_id|**nvarchar(32)**|L'id della query corrente o all'ultima query eseguire (se la sessione è terminata ed è stata eseguita la query in fase di terminazione). Chiave per la visualizzazione.|Valore univoco in tutte le sessioni nel sistema.|  
|status|**nvarchar(10)**|Per le sessioni correnti, indica se la sessione è attualmente attivo o inattivo. Per le sessioni precedenti, la sessione potrebbe mostrare lo stato chiuso o terminato (se forzare la chiusura della sessione).|'ACTIVE', 'CHIUSO', 'INATTIVO', 'TERMINATA'|  
|request_id|**nvarchar(32)**|L'id della query corrente o ultima esecuzione di query.|Valore univoco in tutte le richieste nel sistema. Null se non è stato eseguito.|  
|security_id|**varbinary(85)**|ID di sicurezza dell'entità che esegue la sessione.||  
|login_name|**nvarchar(128)**|Il nome di account di accesso dell'entità che esegue la sessione.|Qualsiasi stringa conforme alle convenzioni di denominazione di utente.|  
|login_time|**datetime**|Data e ora in cui l'utente connesso e questa sessione è stata creata.|Valido **datetime** prima dell'ora corrente.|  
|query_count|**int**|Acquisisce il numero di query/richiesteQuesta sessione è stata eseguita dal momento della creazione.|Maggiore o uguale a 0.|  
|is_transactional|**bit**|Acquisisce se una sessione è attualmente in una transazione oppure No.|0 per la modalità di commit automatico, 1 per transazionale.|  
|client_id|**nvarchar(255)**|Acquisisce informazioni client per la sessione.|Qualsiasi stringa valida.|  
|APP_NAME|**nvarchar(255)**|Acquisisce informazioni sul nome dell'applicazione, facoltativamente, impostare come parte del processo di connessione.|Qualsiasi stringa valida.|  
|sql_spid|**int**|Il numero di id dello SPID. Utilizzare il `session_id` questa sessione. Utilizzare il `sql_spid` colonna di join per **sys.dm_pdw_nodes_exec_sessions**.<br /><br /> **\*\* Avviso \* \***  questa colonna contiene SPID chiuso.||  
  
 Per informazioni sulle righe massimi mantenuto da questa vista, vedere la sezione valori massimi vista di sistema nel [valori minimo e massimo (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9) argomento.  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'autorizzazione `VIEW SERVER STATE`.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel Data Warehouse, viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
