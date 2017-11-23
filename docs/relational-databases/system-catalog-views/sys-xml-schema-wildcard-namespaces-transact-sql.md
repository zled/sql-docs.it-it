---
title: xml_schema_wildcard_namespaces (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_schema_wildcard_namespaces_TSQL
- xml_schema_wildcard_namespaces
- sys.xml_schema_wildcard_namespaces_TSQL
- sys.xml_schema_wildcard_namespaces
dev_langs: TSQL
helpviewer_keywords: sys.xml_schema_wildcard_namespaces catalog view
ms.assetid: a3caa932-41c7-48a9-9b2d-ff090afbb66b
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a268090c284b12142de49d133ece2fbb95dbe4c0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysxmlschemawildcardnamespaces-transact-sql"></a>sys.xml_schema_wildcard_namespaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per spazio dei nomi enumerato per un carattere jolly di XML Schema.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|ID del componente di XML Schema (carattere jolly) a cui viene applicato.|  
|**spazio dei nomi**|**nvarchar(4000)**|Nome o URI dello spazio dei nomi utilizzato dal carattere jolly XML.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML Schema &#40; Sistema di tipi XML &#41; Viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
