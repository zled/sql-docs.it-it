---
title: assembly_files (Transact-SQL) | Documenti Microsoft
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
- sys.assembly_files
- assembly_files_TSQL
- assembly_files
- sys.assembly_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_files catalog view
ms.assetid: 1a384a2c-5556-4d12-a2ba-4da781363143
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 913d4f23f256eb26616ea1c0b3cfae5ca9a9493b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysassemblyfiles-transact-sql"></a>sys.assembly_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni file che compone un assembly.  
    
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|ID dell'assembly a cui appartiene il file.|  
|**name**|**nvarchar(260)**|Nome del file di assembly.|  
|**file_id**|**int**|ID del file. Valore univoco all'interno di un assembly. Il valore 1 per l'ID di file rappresenta la DLL dell'assembly.|  
|**content**|**varbinary(max)**|Contenuto del file.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di Assembly CLR &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
