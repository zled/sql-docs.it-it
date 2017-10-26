---
title: Impostare l'opzione di database AUTO_CLOSE su OFF | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 73fa69efa2d294b0f77de1b93c861f8d3b071ab0
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="set-the-autoclose-database-option-to-off"></a>Impostazione dell'opzione di database AUTO_CLOSE su OFF
  Questa regola consente di controllare se l'opzione di database AUTO_ CLOSE è impostata su OFF. Se impostata su ON, l'opzione AUTO_CLOSE può provocare una riduzione delle prestazione nei database cui si accede di frequente a causa dell'aumento di overhead dovuto all'apertura e alla chiusura del database dopo ogni connessione. L'opzione AUTO_CLOSE comporta anche lo scaricamento della cache delle procedure dopo ogni connessione.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Impostare l'opzione AUTO_CLOSE su OFF per i database cui si accede di frequente.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Opzioni ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  

