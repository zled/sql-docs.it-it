---
title: Sys.fulltext_index_catalog_usages (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fulltext_index_catalog_usages
- sys.fulltext_index_catalog_usages_TSQL
- fulltext_index_catalog_usages
- fulltext_index_catalog_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_index_catalog_usages catalog view
ms.assetid: d095ab62-270b-484b-a541-9f9e7c951cf0
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 87fe6d23d40b82d89fc59daaccc885e22a3c657b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysfulltextindexcatalogusages-transact-sql"></a>sys.fulltext_index_catalog_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni catalogo full-text in riferimento all'indice full-text.    
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID della tabella con indicizzazione full-text. Valore univoco all'interno del database.|  
|**index_id**|**int**|ID dell'indice full-text.|  
|**fulltext_catalog_id**|**int**|ID del catalogo full-text.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Spazi dei dati &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
