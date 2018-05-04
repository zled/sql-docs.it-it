---
title: Sys. Foreign_Keys (Transact-SQL) | Documenti Microsoft
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
- foreign_keys
- sys.foreign_keys
- sys.foreign_keys_TSQL
- foreign_keys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.foreign_keys catalog view
ms.assetid: e960df1a-13fc-43ee-ba91-34c1b719ac2c
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 445d885f0d0458353a124fd02b0c96ced9544ac6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysforeignkeys-transact-sql"></a>sys.foreign_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una riga per ogni oggetto che rappresenta un vincolo di chiave esterna, con **sys.object.type** = F.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**\<Colonne ereditate da Sys. Objects >**||Per un elenco delle colonne ereditate da questa vista, vedere [Sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**referenced_object_id**|**int**|ID dell'oggetto a cui viene fatto riferimento.|  
|**key_index_id**|**int**|ID della chiave di indice all'interno dell'oggetto a cui viene fatto riferimento.|  
|**is_disabled**|**bit**|Il vincolo FOREIGN KEY è disabilitato.|  
|**is_not_for_replication**|**bit**|Il vincolo FOREIGN KEY è stato creato con l'opzione NOT FOR REPLICATION.|  
|**is_not_trusted**|**bit**|Il vincolo FOREIGN KEY non è stato verificato dal sistema.|  
|**delete_referential_action**|**tinyint**|Operazione referenziale dichiarata per il vincolo FOREIGN KEY in caso di eliminazione.<br /><br /> 0 = Nessuna operazione<br /><br /> 1 = Propagazione<br /><br /> 2 = Impostazione su Null<br /><br /> 3 = Impostazione del valore predefinito|  
|**delete_referential_action_desc**|**nvarchar(60)**|Descrizione dell'operazione referenziale dichiarata per il vincolo FOREIGN KEY in caso di eliminazione:<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**update_referential_action**|**tinyint**|Operazione referenziale dichiarata per il vincolo FOREIGN KEY in caso di aggiornamento.<br /><br /> 0 = Nessuna operazione<br /><br /> 1 = Propagazione<br /><br /> 2 = Impostazione su Null<br /><br /> 3 = Impostazione del valore predefinito|  
|**update_referential_action_desc**|**nvarchar(60)**|Descrizione dell'operazione referenziale dichiarata per il vincolo FOREIGN KEY in caso di aggiornamento:<br /><br /> NO_ACTION<br /><br /> CASCADE<br /><br /> SET_NULL<br /><br /> SET_DEFAULT|  
|**is_system_named**|**bit**|1 = Nome generato dal sistema.<br /><br /> 0 = Nome specificato dall'utente.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query nel catalogo di sistema di SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
