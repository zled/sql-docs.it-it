---
title: Sys. endpoint_webmethods (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.endpoint_webmethods_TSQL
- sys.endpoint_webmethods
- endpoint_webmethods_TSQL
- sys.http_soap_methods_TSQL
- endpoint_webmethods
- sys.http_soap_methods
dev_langs:
- TSQL
helpviewer_keywords:
- sys.endpoint_webmethods catalog view
ms.assetid: 7dad0cf6-eafa-47cf-98cc-75ba8d3c7959
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 93053b36893b6812128d2bb397a656d395f839af
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sysendpointwebmethods-transact-sql"></a>sys.endpoint_webmethods (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 Contiene una riga per ogni metodo SOAP definito in un endpoint HTTP abilitato per SOAP. La combinazione delle colonne endpoint_id e spazio dei nomi è univoca.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|endpoint_id|**int**|ID dell'endpoint in base al quale è definito il metodo Web.|  
|spazio dei nomi|**nvarchar (384)**|Spazio dei nomi per il metodo Web.|  
|method_alias|**nvarchar (64)**|Alias del metodo.<br /><br /> Nota: [!INCLUDE[tsql](../../includes/tsql-md.md)] identificatori consentono i caratteri che non sono validi nei nomi di metodo WSDL.<br /><br /> L'alias viene utilizzato per eseguire il mapping del nome esposto nella descrizione WSDL dell'endpoint all'effettivo oggetto eseguibile [!INCLUDE[tsql](../../includes/tsql-md.md)] sottostante richiamato quando viene eseguita la chiamata al metodo Web.|  
|object_name|**nvarchar(776)**|Nome dell'oggetto al quale il metodo Web è reindirizzato, come specificato dall'opzione NAME =. Parti del nome sono separate da un punto (.) e delimitate tramite parentesi quadre, `[``]`.<br /><br /> Il nome dell'oggetto deve essere composto da tre parti, come specificato dall'opzione WSDL.|  
|result_schema|**tinyint**|Opzione che determina l'eventuale schema XSD inviato assieme a una risposta.<br /><br /> 0 = Nessuno<br /><br /> 1 = Standard<br /><br /> 2 = Predefinito|  
|result_schema_desc|**nvarchar(60)**|Descrizione dell'opzione che determina l'eventuale schema XSD inviato assieme a una risposta.<br /><br /> Nessuno<br /><br /> STANDARD<br /><br /> DEFAULT|  
|result_format|**tinyint**|Opzione che determina il formato dei risultati nella risposta.<br /><br /> 1 = ALL_RESULTS<br /><br /> 2 = ROWSETS_ONLY<br /><br /> 3 = NESSUNO|  
|result_format_desc|**nvarchar(60)**|Descrizione dell'opzione che determina il formato dei risultati nella risposta.<br /><br /> ALL_RESULTS<br /><br /> ROWSETS_ONLY<br /><br /> Nessuno|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo degli endpoint &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
