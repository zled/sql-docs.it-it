---
title: Sys.type_assembly_usages (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.type_assembly_usages
- sys.type_assembly_usages_TSQL
- type_assembly_usages_TSQL
- type_assembly_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.type_assembly_usages catalog view
ms.assetid: 79b8bf25-6e4e-4a07-ae93-7a4e44f65171
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 957820cc4bb5ee5e4a2f0f403f054fba7b205d78
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219882"
---
# <a name="systypeassemblyusages-transact-sql"></a>sys.type_assembly_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per tipo relativa al riferimento all'assembly.  
  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**user_type_id**|**int**|ID del tipo.<br /><br /> Per restituire il nome del tipo, creare un join al [Sys. Types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) vista per la colonna del catalogo.|  
|**assembly_id**|**int**|ID dell'assembly.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** . Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di tipi scalari &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
