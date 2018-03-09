---
title: Impostare l'opzione di database AUTO_CLOSE su OFF | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5a2bb33aad433bb0fe962f8a94d139c40aed61e9
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="set-the-autoclose-database-option-to-off"></a>Impostazione dell'opzione di database AUTO_CLOSE su OFF
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questa regola consente di controllare se l'opzione di database AUTO_ CLOSE è impostata su OFF. Se impostata su ON, l'opzione AUTO_CLOSE può provocare una riduzione delle prestazione nei database cui si accede di frequente a causa dell'aumento di overhead dovuto all'apertura e alla chiusura del database dopo ogni connessione. L'opzione AUTO_CLOSE comporta anche lo scaricamento della cache delle procedure dopo ogni connessione.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione AUTO_CLOSE su OFF per i database cui si accede di frequente.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
