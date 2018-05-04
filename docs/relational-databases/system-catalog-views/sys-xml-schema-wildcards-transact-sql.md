---
title: sys.xml_schema_wildcards (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_wildcards
- sys.xml_schema_wildcards_TSQL
- xml_schema_wildcards
- xml_schema_wildcards_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_wildcards catalog view
ms.assetid: 7cedfe9a-e99e-4777-8a28-98674b6e5cff
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e6c9b8d01e6204c7b0e454360a95f6febfcb7df5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysxmlschemawildcards-transact-sql"></a>sys.xml_schema_wildcards (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni componente di XML schema che è un carattere jolly dell'attributo (**tipo** di **V**) o carattere jolly dell'elemento (**tipo** di **W**), entrambi con **symbol_space** di **N**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**\<colonne ereditate >**||Eredita le colonne da [xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**process_content**|**char(1)**|Indica la modalità di elaborazione del contenuto.<br /><br /> S = Convalida di tipo strict (convalida obbligatoria)<br /><br /> L = Convalida di tipo lax (convalida se possibile)<br /><br /> P = Convalida di tipo skip|  
|**process_content_desc**|**nvarchar(60)**|Descrizione della modalità di elaborazione del contenuto:<br /><br /> **STRICT_VALIDATION**<br /><br /> **LAX_VALIDATION**<br /><br /> **SKIP_VALIDATION**|  
|**disallow_namespaces**|**bit**|0 = gli spazi dei nomi enumerati in [xml_schema_wildcard_namespaces](../../relational-databases/system-catalog-views/sys-xml-schema-wildcard-namespaces-transact-sql.md) sono soli quelli consentiti.<br /><br /> 1 = Gli spazi dei nomi sono gli unici disabilitati.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML schema &#40;sistema di tipi XML&#41; viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
