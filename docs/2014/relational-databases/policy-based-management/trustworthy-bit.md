---
title: Bit relativo alla proprietà trustworthy | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 524c1c330288579649fd7744366cf8f3866fe8a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072111"
---
# <a name="trustworthy-bit"></a>Bit relativo alla proprietà trustworthy
  Questa regola consente di determinare se il ruolo dbo per un database è assegnato al ruolo predefinito del server sysadmin e se per il database il bit relativo alla proprietà trustworthy è impostato su ON.  
  
 Se queste condizioni vengono soddisfatte, un utente di database con privilegi potrà elevare il livello di privilegi al ruolo sysadmin. In questo ruolo l'utente può creare ed eseguire assembly non protetti che potrebbero danneggiare il sistema.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Disattivare il bit relativo alla proprietà trustworthy o revocare le autorizzazioni sysadmin al ruolo del database dbo.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
