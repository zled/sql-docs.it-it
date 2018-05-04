---
title: Sys.external_tables (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
ms.assetid: fac4720c-b679-4ab2-864b-ff7810a9b559
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 53e30403430eed3786d815d604ed5ba3b7c2768c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysexternaltables-transact-sql"></a>sys.external_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Contiene una riga per ogni tabella esterna nel database corrente.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|\<colonne ereditate >||Per un elenco delle colonne ereditate da questa vista, vedere [Sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).||  
|max_column_id_used|**int**|ID di colonna massimo utilizzato per questa tabella.||  
|uses_ansi_nulls|**bit**|La tabella è stata creata con l'opzione di database SET ANSI_NULLS impostata su ON.||  
|data_source_id|**int**|ID di oggetto per l'origine dati esterna.||  
|file_format_id|**int**|Per le tabelle esterne su un'origine dati esterna HADOOP, questo è l'ID di oggetto per il formato di file esterno.||  
|posizione|**nvarchar(4000)**|Per le tabelle esterne su un'origine dati esterna HADOOP, questo è il percorso dei dati esterni in HDFS.||  
|reject_type|**tinyint**|Per le tabelle esterne su un'origine dati esterna HADOOP, questo è il modo in cui le righe rifiutate vengono conteggiate durante l'esecuzione di query su dati esterni.|VALORE: il numero di righe rifiutate.<br /><br /> Percentuale: la percentuale di righe rifiutate.|  
|reject_value|**float**|Per le tabelle esterne su un'origine dati esterna di HADOOP:<br /><br /> Per *reject_type =* valore, questo è il numero di rifiuti di riga per consentire prima di aver eseguito la query.<br /><br /> Per *reject_type* = percentuale, indica la percentuale di rifiuti di riga per consentire prima di aver eseguito la query.||  
|reject_sample_value|**int**|Per *reject_type* = percentuale, il numero di righe da caricare, l'esito positivo o negativo, prima di calcolare la percentuale di righe rifiutate.|NULL se reject_type = valore.|  
|distribution_type|**int**|Per le tabelle esterne su un'origine dei dati esterne SHARD_MAP_MANAGER, questa è la distribuzione dei dati delle righe tra le tabelle di base sottostante.|0 – Sharded<br /><br /> 1 – replicati<br /><br /> 2 – Round robin|  
|distribution_desc|**nvarchar(120)**|Per le tabelle esterne su un'origine dei dati esterne SHARD_MAP_MANAGER, si tratta del tipo di distribuzione visualizzato sotto forma di stringa.||  
|sharding_column_id|**int**|Per le tabelle esterne su un'origine dei dati esterne SHARD_MAP_MANAGER e una distribuzione partizionata, questa è l'ID di colonna della colonna che contiene i valori di chiave di partizionamento orizzontale.||  
|remote_schema_name|**sysname**|Per le tabelle esterne su un'origine dei dati esterne SHARD_MAP_MANAGER, questo è lo schema in cui si trova la tabella di base sui database remoti (se diverso da quello in cui è definita nella tabella esterna).||  
|remote_object_name|**sysname**|Per le tabelle esterne su un'origine dei dati esterne SHARD_MAP_MANAGER, questo è il nome della tabella di base sui database remoti (se diverso dal nome della tabella esterna).||  
  
## <a name="permissions"></a>Autorizzazioni  
 La visibilità dei metadati nelle viste del catalogo è limitata alle entità a protezione diretta di cui l'utente è proprietario o per le quali dispone di autorizzazioni. Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)   
 [sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)   
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  
