---
title: Sys. Parameters (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sys.parameters_TSQL
- sys.parameters
- parameters
- parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.parameters catalog view
- table-valued parameters,sys.parameters
ms.assetid: 24e2764b-c8e5-4322-97a4-7407d8b8a92b
caps.latest.revision: 49
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c1f396bb4f31194a79bb1c9d9fffd1b4fee82d98
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysparameters-transact-sql"></a>sys.parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Include una riga per ogni parametro di un oggetto che accetta i parametri. Se l'oggetto è una funzione scalare, è presente anche una riga singola che descrive il valore restituito. Riga avrà un **parameter_id** valore pari a 0.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto a cui appartiene il parametro.|  
|**name**|**sysname**|Nome del parametro. Valore univoco all'interno dell'oggetto.<br /><br /> Se l'oggetto è una funzione scalare, il nome del parametro è una stringa vuota nella riga che rappresenta il valore restituito.|  
|**parameter_id**|**int**|ID del parametro. Valore univoco all'interno dell'oggetto.<br /><br /> Se l'oggetto è una funzione scalare, **parameter_id** = 0 rappresenta il valore restituito.|  
|**system_type_id**|**tinyint**|ID del tipo di sistema del parametro.|  
|**user_type_id**|**int**|ID del tipo di parametro definito dall'utente.<br /><br /> Per restituire il nome del tipo, creare un join al [Sys. Types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) vista per la colonna del catalogo.|  
|**max_length**|**smallint**|Lunghezza massima del parametro, in byte.<br /><br /> Valore = -1 quando il tipo di dati della colonna è **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, o **xml**.|  
|**precisione**|**tinyint**|Precisione del parametro se numerica. In caso contrario 0.|  
|**scala**|**tinyint**|Scala del parametro se numerica. In caso contrario 0.|  
|**is_output**|**bit**|1 = il parametro è OUTPUT o RETURN. In caso contrario, è 0.|  
|**is_cursor_ref**|**bit**|1 = Il parametro è un parametro di riferimento a un cursore.|  
|**has_default_value**|**bit**|1 = il parametro ha un valore predefinito.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta i valori predefiniti solo per gli oggetti CLR in questa vista del catalogo. Il valore di questa colonna è pertanto 0 per gli oggetti [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per visualizzare il valore predefinito di un parametro in un [!INCLUDE[tsql](../../includes/tsql-md.md)] dell'oggetto, eseguire una query di **definizione** colonna del [Sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) vista del catalogo o utilizzare il [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)funzione di sistema.|  
|**is_xml_document**|**bit**|1 = Il contenuto è un documento XML completo.<br /><br /> 0 = il contenuto è un frammento di documento o il tipo di dati della colonna non è **xml**.|  
|**default_value**|**sql_variant**|Se **has_default_value** è 1, il valore di questa colonna è il valore predefinito per il parametro; in caso contrario, NULL.|  
|**xml_collection_id**|**int**|Diverso da zero se il tipo di dati del parametro è **xml** e XML è tipizzato. Il valore è l'ID della raccolta contenente lo spazio dei nomi XML Schema di convalida del parametro.<br /><br /> 0 = Nessuna raccolta di XML Schema.|  
|**is_readonly**|**bit**|1 = il parametro è READONLY; in caso contrario, 0.|  
|**is_nullable**|**bit**|1 = il parametro ammette i valori Null. (Valore predefinito).<br /><br /> 0 = il parametro non ammette i valori Null, per una esecuzione più efficiente delle stored procedure compilate in modo nativo.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [L'esecuzione di query il catalogo di sistema SQL Server domande frequenti](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Sys.all_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-parameters-transact-sql.md)   
 [Sys. system_parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-parameters-transact-sql.md)  
  
  
