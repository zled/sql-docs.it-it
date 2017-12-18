---
title: "Bit relativo alla proprietà trustworthy | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
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
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dedc2b7f2fca8fa796438b40ade32cf21d014286
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="trustworthy-bit"></a>Bit relativo alla proprietà trustworthy
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questa regola determina se il ruolo dbo per un database è assegnato al ruolo predefinito del server sysadmin e se per il database il bit relativo alla proprietà trustworthy è impostato su ON.  
  
 Se queste condizioni vengono soddisfatte, un utente di database con privilegi potrà elevare il livello di privilegi al ruolo sysadmin. In questo ruolo l'utente può creare ed eseguire assembly non protetti che potrebbero danneggiare il sistema.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Disattivare il bit relativo alla proprietà trustworthy o revocare le autorizzazioni sysadmin al ruolo del database dbo.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
