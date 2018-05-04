---
title: Sys. partition_parameters (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
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
f1_keywords:
- partition_parameters_TSQL
- partition_parameters
- sys.partition_parameters_TSQL
- sys.partition_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_parameters catalog view
ms.assetid: 2012ed9d-3ea3-4c29-9b78-dfa54a392dce
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d829b581083cdb434270a58aa276404050011882
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="syspartitionparameters-transact-sql"></a>sys.partition_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Contiene una riga per ogni parametro di una funzione di partizione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**function_id**|**int**|ID della funzione di partizione a cui appartiene il parametro.|  
|**parameter_id**|**int**|ID del parametro. Valore univoco all'interno della funzione di partizione, a partire da 1.|  
|**system_type_id**|**tinyint**|ID del tipo di sistema del parametro. Corrisponde al **system_type_id** colonna il **Sys. Types** vista del catalogo.|  
|**max_length**|**smallint**|Lunghezza massima del parametro in byte.|  
|**precisione**|**tinyint**|Precisione del parametro se numerica. In caso contrario 0.|  
|**scala**|**tinyint**|Scala del parametro se numerica. In caso contrario 0.|  
|**nome_regole_di_confronto**|**sysname**|Nome delle regole di confronto del parametro, se di tipo carattere. In caso contrario, NULL.|  
|**user_type_id**|**int**|ID del tipo. Valore univoco all'interno del database. Per i tipi di dati di sistema, **user_type_id** = **system_type_id**.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo delle funzioni di partizione &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.partition_functions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [Sys.partition_range_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)  
  
  
