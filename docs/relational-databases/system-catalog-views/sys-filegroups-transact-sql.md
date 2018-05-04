---
title: Sys. FileGroups (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 05/24/2016
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
- sys.filegroups_TSQL
- filegroups
- sys.filegroups
- filegroups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filegroups catalog view
ms.assetid: 9e851f72-1f8e-4515-a25d-152ebc12ed56
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8a972d10b1e557793c235bf612255988a3b5de83
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysfilegroups-transact-sql"></a>sys.filegroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una riga per ogni spazio dei dati che costituisce un filegroup.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**\<colonne ereditate >**|--|Per un elenco delle colonne ereditate da questa vista, vedere [data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md).|  
|**filegroup_guid**|**uniqueidentifier**|GUID del filegroup.<br /><br /> NULL = Filegroup PRIMARY|  
|**log_filegroup_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questo valore è NULL.|  
|**is_read_only**|**bit**|1 = Il filegroup è di sola lettura.<br /><br /> 0 = Il filegroup è di lettura/scrittura.|  
|**is_autogrow_all_files**|**bit**|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> 1 = in caso di un file nel filegroup soddisfa la soglia di aumento automatico delle dimensioni, tutti i file nel filegroup di aumento delle dimensioni.<br /><br /> 0 = in caso di un file nel filegroup soddisfa aumenta la soglia di aumento automatico delle dimensioni, solo tale file. Impostazione predefinita.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** . Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Spazi dei dati &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
