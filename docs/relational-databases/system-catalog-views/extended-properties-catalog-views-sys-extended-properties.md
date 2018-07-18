---
title: Sys. extended_properties (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.extended_properties
- sys.extended_properties_TSQL
- extended_properties
- extended_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.extended_properties catalog view
ms.assetid: 439b7299-dce3-4d26-b1c7-61be5e0df82a
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fb0a4c9692b88ccc895d9aa97f4520cc2d5aea4a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="extended-properties-catalog-views---sysextendedproperties"></a>Viste del catalogo delle proprietà - estesi Sys. extended_properties
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Restituisce una riga per ogni proprietà estesa nel database corrente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|class|**tinyint**|Identifica la classe di elementi in cui è inclusa la proprietà. I possibili valori sono i seguenti:<br /><br /> 0 = Database<br /><br /> 1 = Oggetto o colonna<br /><br /> 2 = Parametro<br /><br /> 3 = Schema<br /><br /> 4 = Entità database<br /><br /> 5 = Assembly<br /><br /> 6 = Tipo<br /><br /> 7 = indice<br /><br /> 10 = Raccolta di XML Schema<br /><br /> 15 = Tipo di messaggio<br /><br /> 16 = Contratto di servizio<br /><br /> 17 = Servizio<br /><br /> 18 = Associazione al servizio remoto<br /><br /> 19 = Route<br /><br /> 20 = Spazio dati (schema di partizione o filegroup)<br /><br /> 21 = Funzione di partizione<br /><br /> 22 = File di database<br /><br /> 27 = Guida di piano|  
|class_desc|**nvarchar(60)**|Descrizione della classe in cui è inclusa la proprietà estesa. I possibili valori sono i seguenti:<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN<br /><br /> Parametro<br /><br /> SCHEMA<br /><br /> DATABASE_PRINCIPAL<br /><br /> ASSEMBLY<br /><br /> TYPE<br /><br /> INDEX<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> MESSAGE_TYPE<br /><br /> SERVICE_CONTRACT<br /><br /> SERVICE<br /><br /> REMOTE_SERVICE_BINDING<br /><br /> ROUTE<br /><br /> DATASPACE<br /><br /> PARTITION_FUNCTION<br /><br /> DATABASE_FILE<br /><br /> PLAN_GUIDE|  
|major_id|**int**|ID dell'elemento in cui è inclusa la proprietà estesa, interpretato in base alla classe di appartenenza. Per la maggior parte degli elementi, questo ID si applica a ciò che rappresenta la classe. L'interpretazione per gli ID principali non standard è la seguente:<br /><br /> Se la classe è 0, major_id è sempre 0.<br /><br /> Se la classe è 1, 2 o 7, major_id è object_id.|  
|minor_id|**int**|ID secondario dell'elemento in cui è inclusa la proprietà estesa, interpretato in base alla classe di appartenenza. Per la maggior parte degli elementi corrisponde a 0. Negli altri casi i possibili valori sono i seguenti:<br /><br /> Se la classe è 1, minor_id è column_id se colonna, altrimenti 0 se oggetto.<br /><br /> Se la classe è 2, minor_id è parameter_id.<br /><br /> Se la classe è 7, minor _id è index_id.|  
|name|**sysname**|Nome della proprietà, univoco con class, major_id e minor_id.|  
|Valore|**sql_variant**|Valore della proprietà estesa.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo delle proprietà estese &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/f39fd324-efd4-4468-884c-bf77ed1a026f)   
 [Sys.fn_listextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)  
  
  
