---
title: Ricicla log degli errori di SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e966fcf544ace7a719d4760c366c69fe91b892f5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36055612"
---
# <a name="recycle-sql-server-agent-error-logs"></a>Ricicla log degli errori di SQL Server Agent
  Utilizzare questa pagina per riciclare i log degli errori di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Il riciclo dei log chiude il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e avvia un nuovo registro errori senza riavviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Si noti che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent mantiene gli ultimi nove log degli errori. Se esistono già nove log degli errori, il riciclo causa l'eliminazione del log degli errori meno recente da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="see-also"></a>Vedere anche  
 [Log degli errori di SQL Server Agent](sql-server-agent-error-log.md)  
  
  