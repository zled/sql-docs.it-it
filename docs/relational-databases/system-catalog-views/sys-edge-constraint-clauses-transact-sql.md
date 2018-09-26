---
title: Sys.edge_constraint_clauses (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.edge_constraint_clauses
- edge_constraint_clauses
- SQL Graph
- edge_constraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.edge_constraint_clauses catalog view
ms.assetid: 0f782d2f-7126-46ab-85b7-bcba44862231
caps.latest.revision: 1
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c30bbe0be0921183e1b417d707b057420cb072e3
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2018
ms.locfileid: "46715126"
---
# <a name="sysedgeconstraintclauses-transact-sql"></a>Sys.edge_constraint_clauses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx.md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Contiene una riga per ogni clausola di un vincolo di arco.
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|object_id del vincolo di arco.|  
|**from_object_id**|**int**|object_id della tabella nodi FROM.|  
|**to_object_id**|**int**|object_id della tabella a nodo.|  
|**clause_number**|**int**|Indice generato internamente integer nella clausola.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query nel catalogo di sistema di SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
