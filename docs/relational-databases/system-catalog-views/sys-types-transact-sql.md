---
title: Sys. Types (Transact-SQL) | Documenti Microsoft
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
- types
- types_TSQL
- sys.types_TSQL
- sys.types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.types catalog view
- table-valued parameters,sys.types
ms.assetid: a5dbc842-71a0-4f62-b5e0-f560a99b7f8c
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0e474a164ce837ccf2ea965ae3590921461d3bce
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="systypes-transact-sql"></a>sys.types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una riga per ogni tipo di sistema e definito dall'utente.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del tipo. Valore univoco all'interno dello schema.|  
|**system_type_id**|**tinyint**|ID del tipo di sistema interno del tipo.|  
|**user_type_id**|**int**|ID del tipo. Valore univoco all'interno del database. Per i tipi di dati di sistema, **user_type_id** = **system_type_id**.|  
|**schema_id**|**int**|ID dello schema a cui appartiene il tipo.|  
|**principal_id**|**int**|ID del proprietario, se diverso dal proprietario dello schema. Per impostazione predefinita, gli oggetti contenuti nello schema appartengono al proprietario dello schema stesso. È tuttavia possibile specificare un altro proprietario modificando la proprietà mediante l'istruzione ALTER AUTHORIZATION.<br /><br /> NULL se non esiste un proprietario alternativo.|  
|**max_length**|**smallint**|Lunghezza massima (in byte) del tipo.<br /><br /> -1 = la colonna è di tipo di dati **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, o **xml**.<br /><br /> Per **testo** colonne, il **max_length** valore sarà 16.|  
|**precisione**|**tinyint**|Precisione massima del tipo se numerica. In caso contrario 0.|  
|**scala**|**tinyint**|Scala massima del tipo se numerica. In caso contrario 0.|  
|**nome_regole_di_confronto**|**sysname**|Nome delle regole di confronto del tipo se di tipo carattere. In caso contrario NULL.|  
|**is_nullable**|**bit**|Il tipo ammette valori Null.|  
|**is_user_defined**|**bit**|1 = Tipo definito dall'utente.<br /><br /> 0 = Tipo di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**is_assembly_type**|**bit**|1 = L'implementazione del tipo è definita in un assembly CLR.<br /><br /> 0 = Il tipo è basato su un tipo di dati di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**default_object_id**|**int**|ID dell'oggetto predefinito autonomo associato al tipo tramite [sp_bindefault](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md).<br /><br /> 0 = Non esistono oggetti predefiniti.|  
|**rule_object_id**|**int**|ID della regola autonoma associata al tipo utilizzando [sp_bindrule](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md).<br /><br /> 0 = Non esistono regole.|  
|**is_table_type**|**bit**|Indica che il tipo è una tabella.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo di tipi scalari &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query nel catalogo di sistema di SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
