---
title: Impostare l'opzione di database AUTO_SHRINK su OFF | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f5e28b02301c50d41e15654250f36f0779f6858f
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="set-the-autoshrink-database-option-to-off"></a>Impostazione dell'opzione di database AUTO_SHRINK su OFF
  Questa regola consente di controllare se l'opzione di database AUTO_SHRINK è impostata su OFF. La compattazione e l'espansione di un database comportano spesso la frammentazione fisica.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione di database AUTO_SHRINK su OFF. Se si prevede che lo spazio recuperato non sarà necessario in futuro, è possibile liberare spazio compattando manualmente il database.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 Articolo [315512](http://go.microsoft.com/fwlink/?linkid=117750)della Microsoft Knowledge Base  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

