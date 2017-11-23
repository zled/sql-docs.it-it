---
title: Sys.external_data_sources (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 1016db6e-9950-4ae2-a004-bd4171e27359
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b8137f7bf094becc2197b4420aecf81dd8c5c5d
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysexternaldatasources-transact-sql"></a>Sys.external_data_sources (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Contiene una riga per ogni origine dati esterna nel database corrente per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)], e [!INCLUDE[ssSDW](../../includes/sssdw-md.md)].  
  
 Contiene una riga per ogni origine dati esterna nel server per [!INCLUDE[ssPDW](../../includes/sspdw-md.md)].  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|data_source_id|**int**|ID di oggetto per l'origine dati esterna.||  
|name|**sysname**|Nome dell'origine dati esterna.||  
|posizione|**nvarchar(4000)**|La stringa di connessione, che include il protocollo, indirizzo IP e porta per l'origine dati esterna.||  
|type_desc|**nvarchar(255)**|Tipo di origine di dati visualizzato come una stringa.|HADOOP, RDBMS, SHARD_MAP_MANAGER, RemoteDataArchiveTypeExtDataSource|  
|tipo|**tinyint**|Tipo di origine di dati visualizzato come un numero.|0 - HADOOP<br /><br /> 1 - RDBMS<br /><br /> 2 - SHARD_MAP_MANAGER<br /><br /> 3 - RemoteDataArchiveTypeExtDataSource|  
|resource_manager_location|**nvarchar(4000)**|Per digitare HADOOP, IP e porta percorso di gestione risorse di Hadoop. Viene utilizzato per l'invio di un processo in un'origine dati Hadoop.<br /><br /> NULL per altri tipi di origini dati esterne.||  
|credential_id|**int**|L'ID oggetto del database con ambito credenziale utilizzata per connettersi all'origine dati esterna.||  
|database_name|**sysname**|Per tipo RDBMS, il nome del database remoto. Per tipo, SHARD_MAP_MANAGER, il nome del database di gestione di partizioni della mappa. NULL per altri tipi di origini dati esterne.||  
|shard_map_name|**sysname**|Per tipo SHARD_MAP_MANAGER, il nome della mappa partizioni. NULL per altri tipi di origini dati esterne.||  
  
## <a name="permissions"></a>Permissions  
 La visibilità dei metadati nelle viste del catalogo è limitata alle entità a protezione diretta di cui l'utente è proprietario o per le quali dispone di autorizzazioni. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sys.external_file_formats &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [Sys.external_tables &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)   
 [CREATE EXTERNAL DATA SOURCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md)  
  
  
