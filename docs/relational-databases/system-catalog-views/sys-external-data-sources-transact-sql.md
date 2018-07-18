---
title: sys.external_data_sources (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1016db6e-9950-4ae2-a004-bd4171e27359
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 944a8096c20d6ab825503d4db9f824ba0bbe208e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38001233"
---
# <a name="sysexternaldatasources-transact-sql"></a>sys.external_data_sources (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Contiene una riga per ogni origine dati esterna nel database corrente per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)], e [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 Contiene una riga per ogni origine dati esterna nel server per [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|data_source_id|**int**|ID oggetto per l'origine dati esterna.||  
|NAME|**sysname**|Nome dell'origine dati esterna.||  
|posizione|**nvarchar(4000)**|La stringa di connessione, che include il protocollo, indirizzo IP e porta per l'origine dati esterna.||  
|type_desc|**nvarchar(255)**|Tipo di origine dati visualizzata sotto forma di stringa.|HADOOP, RDBMS, SHARD_MAP_MANAGER, RemoteDataArchiveTypeExtDataSource|  
|Tipo|**tinyint**|Tipo di origine dati visualizzata sotto forma di numero.|0 - HADOOP<br /><br /> 1 - RDBMS<br /><br /> 2 - SHARD_MAP_MANAGER<br /><br /> 3 - RemoteDataArchiveTypeExtDataSource|  
|resource_manager_location|**nvarchar(4000)**|Per digitare HADOOP, l'indirizzo IP e porta percorso di gestione risorse di Hadoop. Viene utilizzato per l'invio di un processo in un'origine dati di Hadoop.<br /><br /> NULL per altri tipi di origini dati esterne.||  
|credential_id|**int**|L'ID oggetto del database con ambito le credenziali usate per connettersi all'origine dati esterna.||  
|database_name|**sysname**|Per il tipo di sistema RDBMS, il nome del database remoto. Per tipo SHARD_MAP_MANAGER, il nome del database di gestione mappe partizioni. NULL per altri tipi di origini dati esterne.||  
|shard_map_name|**sysname**|Per tipo SHARD_MAP_MANAGER, il nome della mappa partizioni. NULL per altri tipi di origini dati esterne.||  
  
## <a name="permissions"></a>Autorizzazioni  
 La visibilità dei metadati nelle viste del catalogo è limitata alle entità a protezione diretta di cui l'utente è proprietario o per le quali dispone di autorizzazioni. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
  
