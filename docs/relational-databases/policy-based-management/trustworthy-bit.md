---
title: "Bit relativo alla proprietà trustworthy | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
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
ms.openlocfilehash: 6a9aeb335d60738a872cfb6ffde9e1c4de4a4158
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="trustworthy-bit"></a>Bit relativo alla proprietà trustworthy
  Questa regola consente di determinare se il ruolo dbo per un database è assegnato al ruolo predefinito del server sysadmin e se per il database il bit relativo alla proprietà trustworthy è impostato su ON.  
  
 Se queste condizioni vengono soddisfatte, un utente di database con privilegi potrà elevare il livello di privilegi al ruolo sysadmin. In questo ruolo l'utente può creare ed eseguire assembly non protetti che potrebbero danneggiare il sistema.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Disattivare il bit relativo alla proprietà trustworthy o revocare le autorizzazioni sysadmin al ruolo del database dbo.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
