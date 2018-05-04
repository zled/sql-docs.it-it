---
title: sys.dm_db_missing_index_details (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_missing_index_details
- dm_db_missing_index_details
- sys.dm_db_missing_index_details_TSQL
- dm_db_missing_index_details_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- missing indexes feature [SQL Server], sys.dm_db_missing_index_details dynamic management view
- sys.dm_db_missing_index_details dynamic management view
ms.assetid: ced484ae-7c17-4613-a3f9-6d8aba65a110
caps.latest.revision: 37
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: caa956a0edacdffd0656871828ba052156425ccc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmdbmissingindexdetails-transact-sql"></a>sys.dm_db_missing_index_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni dettagliate sugli indici mancanti, escludendo gli indici spaziali.  
  
 In [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], le viste a gestione dinamica non possono esporre le informazioni che influenzerebbero l'indipendenza del database o le informazioni sugli altri database a cui l'utente dispone di accesso. Per evitare di esporre queste informazioni, ogni riga che contiene dati che non appartengono al tenant connesso viene esclusa tramite filtro.  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**index_handle**|**int**|Identifica un determinato indice mancante. L'identificatore è univoco nel server. **index_handle** è la chiave di questa tabella.|  
|**database_id**|**smallint**|Identifica il database in cui è archiviata la tabella con l'indice mancante.|  
|**object_id**|**int**|Identifica la tabella in cui l'indice risulta mancante.|  
|**equality_columns**|**nvarchar(4000)**|Elenco delimitato da virgole delle colonne che contribuiscono ai predicati di uguaglianza nel formato seguente:<br /><br /> *table.column* =*constant_value*|  
|**inequality_columns**|**nvarchar(4000)**|Elenco delimitato da virgole delle colonne che contribuiscono ai predicati di disuguaglianza, ad esempio predicati nel formato seguente:<br /><br /> *table.column* > *constant_value*<br /><br /> Qualsiasi operatore di confronto diverso da "=" esprime disuguaglianza.|  
|**included_columns**|**nvarchar(4000)**|Elenco delimitato da virgole delle colonne necessarie come colonne di copertura per la query. Per ulteriori informazioni sulla copertura o le colonne incluse, vedere [creare indici con colonne incluse](../../relational-databases/indexes/create-indexes-with-included-columns.md).<br /><br /> Per gli indici con ottimizzazione per la memoria (sia hash con ottimizzazione per la memoria non cluster), ignorare **included_columns**. Tutte le colonne della tabella vengono incluse in ogni indice ottimizzato per la memoria.|  
|**istruzione**|**nvarchar(4000)**|Nome della tabella in cui l'indice risulta mancante.|  
  
## <a name="remarks"></a>Osservazioni  
 Le informazioni restituite da **Sys.dm db_missing_index_details** viene aggiornato quando una query viene ottimizzata attraverso il query optimizer e non è persistente. Le informazioni relative agli indici mancanti vengono mantenute solo fino al riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per mantenere tali informazioni anche dopo il riciclo del server, gli amministratori di database devono eseguirne periodicamente copie di backup.  
  
 Per determinare il gruppo di indici mancanti a cui un determinato indice mancante, è possibile eseguire una query di **Sys.dm db_missing_index_groups** vista a gestione dinamica appartiene con **Sys.dm db_missing_index_details**  in base il **index_handle** colonna.  
  
## <a name="using-missing-index-information-in-create-index-statements"></a>Utilizzo di informazioni sugli indici mancanti in istruzioni CREATE INDEX  
 Per convertire le informazioni restituite da **Sys.dm db_missing_index_details** in un'istruzione CREATE INDEX per gli indici con ottimizzazione per la memoria sia basata su disco, le colonne di uguaglianza devono essere inserite prima delle colonne di disuguaglianza e insieme deve costituire la chiave dell'indice. Aggiungere le colonne incluse all'istruzione CREATE INDEX mediante la clausola INCLUDE. Per determinare un ordine efficiente per le colonne di uguaglianza, ordinarle in base alla selettività a partire dalle colonne più selettive, all'estrema sinistra nell'elenco di colonne.  
  
 Per ulteriori informazioni sugli indici con ottimizzazione per la memoria, vedere [indici per tabelle con ottimizzazione](../../relational-databases/in-memory-oltp/indexes-for-memory-optimized-tables.md).  
  
## <a name="transaction-consistency"></a>Consistenza delle transazioni  
 Se in una transazione viene creata o eliminata una tabella, le righe contenenti le informazioni sugli indici mancanti per gli oggetti eliminati vengono rimosse da questo oggetto a gestione dinamica, mantenendo la consistenza delle transazioni.  
  
## <a name="permissions"></a>Autorizzazioni

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], richiede il `VIEW DATABASE STATE` autorizzazione per il database.   

## <a name="see-also"></a>Vedere anche  
 [sys.dm_db_missing_index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-columns-transact-sql.md)   
 [sys.dm_db_missing_index_groups &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [sys.dm_db_missing_index_group_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  
