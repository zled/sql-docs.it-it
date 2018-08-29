---
title: Sys. parameter_type_usages (Transact-SQL) | Microsoft Docs
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
- sys.parameter_type_usages
- sys.parameter_type_usages_TSQL
- parameter_type_usages_TSQL
- parameter_type_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.parameter_type_usages catalog view
ms.assetid: af0e167b-bffb-4525-84ec-3607f9268d3d
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 116bec6c18c6b1fe882937913acac09d56550844
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036983"
---
# <a name="sysparametertypeusages-transact-sql"></a>sys.parameter_type_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni parametro del tipo definito dall'utente.  
  
> [!NOTE]  
>  Questa vista non restituisce righe per parametri di procedure numerate.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto a cui appartiene il parametro.|  
|**parameter_id**|**int**|ID del parametro. Valore univoco all'interno dell'oggetto.|  
|**user_type_id**|**int**|ID del tipo definito dall'utente.<br /><br /> Per restituire il nome del tipo, aggiungere il [Sys. Types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) su questa colonna vista del catalogo.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** . Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di tipi scalari &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
