---
title: Sys.column_xml_schema_collection_usages (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- column_xml_schema_collection_usages_TSQL
- sys.column_xml_schema_collection_usages
- column_xml_schema_collection_usages
- sys.column_xml_schema_collection_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_xml_schema_collection_usages catalog view
ms.assetid: 4fd1ec7f-b9dc-4ddb-ab3a-0d59ab05ad20
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c525bf31fc35cff8da571aa28e495c26e2cabb96
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027780"
---
# <a name="syscolumnxmlschemacollectionusages-transact-sql"></a>sys.column_xml_schema_collection_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni colonna convalidata da un XML Schema.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto a cui appartiene la colonna.|  
|**column_id**|**int**|ID della colonna. Valore univoco all'interno dell'oggetto.|  
|**xml_collection_id**|**int**|ID della raccolta contenente lo spazio dei nomi dell'XML Schema di convalida per la colonna.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML schema &#40;sistema di tipi XML&#41; viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
