---
title: Impostare l'opzione di database AUTO_SHRINK su OFF | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
caps.latest.revision: "11"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 91e260a447d022f04bc74268a8243e3993a7ce61
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="set-the-autoshrink-database-option-to-off"></a>Impostazione dell'opzione di database AUTO_SHRINK su OFF
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questa regola controlla se l'opzione di database AUTO_SHRINK è impostata su OFF. La compattazione e l'espansione di un database comportano spesso la frammentazione fisica.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione di database AUTO_SHRINK su OFF. Se si prevede che lo spazio recuperato non sarà necessario in futuro, è possibile liberare spazio compattando manualmente il database.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 Articolo [315512](http://go.microsoft.com/fwlink/?linkid=117750)della Microsoft Knowledge Base  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
