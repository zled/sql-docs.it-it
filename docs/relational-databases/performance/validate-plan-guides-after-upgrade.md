---
title: Convalidare le guide di piano dopo l'aggiornamento | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-plan-guides
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 986538833b7f1b9cc6977449b918997b21828159
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="validate-plan-guides-after-upgrade"></a>Convalidare le guide di piano dopo l'aggiornamento
  Quando si aggiorna l'applicazione a una nuova versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è consigliabile valutare nuovamente e testare le definizioni delle guide di piano. I requisiti di ottimizzazione delle prestazioni e la funzionalità di individuazione delle corrispondenze delle guide di piano possono cambiare. Anche se una guida di piano non valida non farà in modo che una query non riesca, il piano è compilato senza utilizzare la guida di piano e potrebbe non essere la migliore scelta. Dopo aver aggiornato un database a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], si consiglia di eseguire le seguenti attività:  
  
-   Eseguire la convalida delle guide di piano esistenti usando la funzione [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) .  
  
-   Usare gli eventi estesi per eseguire il monitoraggio di piani fuorviati per determinati periodo di tempo usando l'evento [Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) .  
  
  

