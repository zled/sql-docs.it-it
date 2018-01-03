---
title: Ricicla log degli errori di SQL Server Agent | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.errorlog.recyclesqlagenterrorlogs.f1
ms.assetid: 10bc2dd1-0505-4527-8ec7-d3b4e5d6352b
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 349ae61e3ed53912f2f25565f9db7a99f4b56b56
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="recycle-sql-server-agent-error-logs"></a>Ricicla log degli errori di SQL Server Agent
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Usare questa pagina per riciclare i log degli errori di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Il riciclo dei log chiude il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent e avvia un nuovo registro errori senza riavviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Si noti che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent mantiene gli ultimi nove log degli errori. Se esistono già nove log degli errori, il riciclo causa l'eliminazione del log degli errori meno recente da parte di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="see-also"></a>Vedere anche  
[Log degli errori di SQL Server Agent](../../ssms/agent/sql-server-agent-error-log.md)  
  
