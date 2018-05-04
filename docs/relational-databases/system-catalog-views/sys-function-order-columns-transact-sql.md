---
title: sys.function_order_columns (Transact-SQL) | Microsoft Docs
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
- function_order_columns
- sys.function_order_columns_TSQL
- function_order_columns_TSQL
- sys.function_order_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.function_order_columns catalog view
ms.assetid: 29287973-3125-4d35-8ca9-92cb45828854
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 79720c921ad338b5e0a651b97a804c653c21303a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysfunctionordercolumns-transact-sql"></a>sys.function_order_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni colonna che fa parte di un **ordine** espressione di una funzione con valori di tabella di consideriamo language runtime (CLR).  

  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto (funzione CLR con valori di tabella) nel quale è definito l'ordinamento.|  
|**order_column_id**|**int**|ID della colonna di ordinamento. **valore di order_column_id** è univoco solo nell'ambito **object_id**.<br /><br /> **valore di order_column_id** rappresenta la posizione della colonna nell'ordinamento.|  
|**column_id**|**int**|ID della colonna in **object_id**.<br /><br /> **column_id** è univoco solo nell'ambito **object_id**.|  
|**is_descending**|**bit**|1 = Direzione di ordinamento decrescente per la colonna di ordinamento.<br /><br /> 0 = Direzione di ordinamento crescente per la colonna di ordinamento.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
