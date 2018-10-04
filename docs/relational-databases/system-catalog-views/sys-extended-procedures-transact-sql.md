---
title: Sys. extended_procedures (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- extended_procedures
- sys.extended_procedures
- sys.extended_procedures_TSQL
- extended_procedures_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.extended_procedures catalog view
ms.assetid: 310e0f87-0044-4fdf-bd12-51a723a74ce6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8eb0d10f8be8c2e5d9f939dd7a631d22154d6608
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613681"
---
# <a name="sysextendedprocedures-transact-sql"></a>sys.extended_procedures (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni oggetto che rappresenta una stored procedure estesa, con **sys.objects.type** = X. Poiché le stored procedure estese sono installate nel **master** database, sono visibili solo da quel contesto di database. Selezionando il **Sys. extended_procedures** vista in qualsiasi altro contesto di database restituirà un set di risultati vuoto.  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**\<Colonne ereditate da Sys. Objects >**||Per un elenco delle colonne ereditate da questa vista, vedere [Sys. Objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).|  
|**Nome_DLL**|**nvarchar(260)**|Nome, incluso il percorso, della DLL di questa stored procedure estesa.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
