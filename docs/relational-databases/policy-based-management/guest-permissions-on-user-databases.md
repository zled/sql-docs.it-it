---
title: Autorizzazioni Guest nei database utente | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 49a29bf175c9ad048a1243bc4d495bf4be6f0e92
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="guest-permissions-on-user-databases"></a>Autorizzazioni Guest nei database utente
  Questa regola consente di determinare se l'utente guest dispone dell'autorizzazione necessaria per accedere al database. Questa regola si applica solo ai database utente.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
 Se non è necessaria, revocare l'autorizzazione di accesso al database dell'utente guest.  
  
 L'utente guest non può essere rimosso. È tuttavia possibile disabilitarlo revocandone l'autorizzazione CONNECT tramite l'esecuzione di REVOKE CONNECT FROM GUEST all'interno di un database diverso da master, tempdb o msdb.  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Sicurezza di SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e applicare le procedure consigliate tramite la gestione basata su criteri](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
