---
title: fts_outstanding_batches (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_fts_outstanding_batches
- dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches_TSQL
- sys.dm_fts_outstanding_batches
dev_langs:
- TSQL
helpviewer_keywords:
- troubleshooting [SQL Server], full-text search
- sys.dm_fts_outstanding_batches dynamic management view
ms.assetid: c4d697ed-c906-4c28-b137-036a25e13c84
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3001b60dbaf55ed19cd2f226ae827072ed94613f
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43092847"
---
# <a name="sysdmftsoutstandingbatches-transact-sql"></a>sys.dm_fts_outstanding_batches (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni su ogni batch di indicizzazione full-text.  
  
  |Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|ID del database|  
|catalog_id|**int**|ID del catalogo full-text|  
|table_id|**int**|ID della tabella contenente l'indice full-text.|  
|batch_id|**int**|ID batch|  
|memory_address|**varbinary(8)**|Indirizzo di memoria dell'oggetto batch|  
|crawl_memory_address|**varbinary(8)**|Indirizzo di memoria dell'oggetto ricerca per indicizzazione (oggetto padre)|  
|memregion_memory_address|**varbinary(8)**|Indirizzo di una regione di memoria condivisa in uscita dell'host del daemon di filtri (fdhost.exe)|  
|hr_batch|**int**|Codice relativo all'errore più recente per il batch|  
|is_retry_batch|**bit**|Indica se questo è un batch relativo a un tentativo:<br /><br /> 0 = No<br /><br /> 1 = Sì|  
|retry_hints|**int**|Tipo di tentativo necessario per il batch:<br /><br /> 0 = nessun tentativo<br /><br /> 1 = tentativo multi-thread<br /><br /> 2 = tentativo a thread singolo<br /><br /> 3 = tentativo a thread singolo e multi-thread<br /><br /> 5 = tentativo finale multi-thread<br /><br /> 6 = tentativo finale a thread singolo<br /><br /> 7 = tentativo finale a thread singolo e multi-thread|  
|retry_hints_description|**nvarchar(120)**|Descrizione del tipo di tentativo necessario:<br /><br /> NO RETRY<br /><br /> MULTI THREAD RETRY<br /><br /> SINGLE THREAD RETRY<br /><br /> SINGLE AND MULTI THREAD RETRY<br /><br /> MULTI THREAD FINAL RETRY<br /><br /> SINGLE THREAD FINAL RETRY<br /><br /> SINGLE AND MULTI THREAD FINAL RETRY|  
|doc_failed|**bigint**|Numero di documenti con errore nel batch|  
|batch_timestamp|**timestamp**|Valore del timestamp ottenuto al momento della creazione del batch|  
  
## <a name="permissions"></a>Permissions  

Sul [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è necessario `VIEW SERVER STATE` autorizzazione.   
Sul [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], è necessario il `VIEW DATABASE STATE` autorizzazione nel database.   
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rilevato il numero di batch attualmente in elaborazione per ogni tabella nell'istanza del server.  
  
```  
SELECT database_id, table_id, COUNT(*) AS batch_count FROM sys.dm_fts_outstanding_batches GROUP BY database_id, table_id ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica la ricerca semantica e ricerca full-Text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [Ricerca full-text](../../relational-databases/search/full-text-search.md)  
  
  
