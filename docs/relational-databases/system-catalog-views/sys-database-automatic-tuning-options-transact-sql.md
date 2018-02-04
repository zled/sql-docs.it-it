---
title: sys.database_automatic_tuning_options (Transact-SQL) | Microsoft Docs
description: Informazioni su come visualizzare le opzioni di ottimizzazione automatica in un Database SQL
ms.custom: 
ms.date: 07/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- database_automatic_tuning_options_tsql
- database_automatic_tuning_options
- sys.database_automatic_tuning_options_tsql
- sys.database_automatic_tuning_options
dev_langs:
- TSQL
helpviewer_keywords:
- database_automatic_tuning_options catalog view
- sys.database_automatic_tuning_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
caps.latest.revision: 
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4208b9e294273444c24ac9e3a05e60b43d4274c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdatabaseautomatictuningoptions-transact-sql"></a>sys.database\_automatic\_tuning_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Restituisce le opzioni di ottimizzazione automatica per il database.  

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|Il nome dell'opzione di ottimizzazione automatica. Fare riferimento a [ALTER DATABASE SET AUTOMATIC_TUNING &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) per le opzioni disponibili.|  
|**desired_state**|**smallint**|Indica la modalità operativa desiderata per l'opzione di ottimizzazione automatica, impostare in modo esplicito dall'utente.<br />0 = OFF<br />1 = ON|  
|**desired_state_desc**|**nvarchar(60)**|Descrizione testuale della modalità operativa desiderata dell'opzione di ottimizzazione automatica.<br />OFF<br />ON|  
|**actual_state**|**smallint**|Indica la modalità operativa dell'opzione di ottimizzazione automatica.<br />0 = OFF<br />1 = ON|  
|**actual_state_desc**|**nvarchar(60)**|Descrizione testuale della modalità operativa effettiva dell'opzione di ottimizzazione automatica.<br />OFF<br />ON|  
|**reason**|**smallint**|Indica perché effettivi e desiderati stati sono diversi.<br />2 = DISABILITATO<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar(60)**|Descrizione del motivo perché effettivi e desiderati stati sono diversi.<br />DISABILITATO = viene disattivata dal sistema<br />QUERY_STORE_OFF = archivio Query è stata disattivata<br />QUERY_STORE_READ_ONLY = archivio Query è in modalità di sola lettura<br />NOT_SUPPORTED = disponibile solo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition| 
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il `VIEW DATABASE STATE` autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [L'ottimizzazione automatica](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
