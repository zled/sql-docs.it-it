---
title: Ricicla log degli errori di SQL Server Agent | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6b3b79686cbc194eda76fd1f4873d81c26d8d31c
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="recycle-sql-server-agent-error-logs"></a>Ricicla log degli errori di SQL Server Agent
Utilizzare questa pagina per riciclare i log degli errori di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Il riciclo dei log chiude il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent e avvia un nuovo registro errori senza riavviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Si noti che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent mantiene gli ultimi nove log degli errori. Se esistono già nove log degli errori, il riciclo causa l'eliminazione del log degli errori meno recente da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="see-also"></a>Vedere anche  
[Log degli errori di SQL Server Agent](../../ssms/agent/sql-server-agent-error-log.md)  
  

