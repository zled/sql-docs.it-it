---
title: xml_schema_collections (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_collections_TSQL
- sys.xml_schema_collections
- xml_schema_collections
- xml_schema_collections_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.xml_schema_collections catalog view
ms.assetid: f3f7f3dc-029f-4942-ab3c-75fa9814e40f
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 34762896bc35e2eb7dbf79674aca951bceb37a0d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sysxmlschemacollections-transact-sql"></a>sys.xml_schema_collections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni raccolta di XML Schema. Una raccolta di XML Schema è un set denominato di definizioni XSD. La raccolta di XML Schema è a sua volta contenuta in uno schema relazionale e viene identificata da un nome [!INCLUDE[tsql](../../includes/tsql-md.md)] con ambito schema. Le tuple seguenti sono univoche: xml_collection_id, schema_id e name.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|xml_collection_id|**int**|Nome della raccolta di XML Schema. Univoco all'interno del database.|  
|schema_id|**int**|ID dello schema relazionale contenente la raccolta di XML Schema.|  
|principal_id|**int**|ID del singolo proprietario se diverso dal proprietario dello schema. Per impostazione predefinita, gli oggetti contenuti nello schema appartengono al proprietario dello schema stesso. È tuttavia possibile specificare un proprietario alternativo tramite l'istruzione ALTER AUTHORIZATION per modificare la proprietà.<br /><br /> NULL = Nessun proprietario singolo alternativo.|  
|name|**sysname**|Nome della raccolta di XML Schema.|  
|create_date|**datetime**|Data di creazione della raccolta di XML Schema.|  
|modify_date|**datetime**|Data dell'ultima modifica della raccolta di XML Schema.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML Schema &#40; Sistema di tipi XML &#41; Viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query nel catalogo di sistema di SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
