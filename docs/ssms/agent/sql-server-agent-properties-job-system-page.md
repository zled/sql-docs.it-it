---
title: "Proprietà SQL Server Agent (pagina Sistema processi) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1ba6041cd4169bd8c87fbf1e220d91a86ed2fdd1
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-agent-properties-job-system-page"></a>Proprietà SQL Server Agent (pagina Sistema processi)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Usare questa pagina per visualizzare e modificare il modo in cui il servizio [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent gestisce i processi.  
  
## <a name="options"></a>Opzioni  
**Intervallo di timeout chiusura (secondi)**  
Consente di specificare il numero di secondi di attesa del completamento dei processi prima che questi vengano chiusi da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Se il processo è ancora in esecuzione dopo la scadenza dell'intervallo specificato, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent lo arresterà in modo forzato.  
  
**Usa account proxy non amministratore**  
Imposta un account proxy non amministratore per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] e versioni successive supportano più proxy, pertanto questa opzione è applicabile unicamente quando si gestiscono le versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent precedenti a [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Nome utente**  
Digitare il nome dell'utente per l'account proxy non amministratore. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] supporta più proxy, pertanto questa opzione è applicabile unicamente quando si gestiscono versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent precedenti a [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
**Password**  
Digitare la password dell'utente per l'account proxy non amministratore. [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] e versioni successive supportano più proxy, pertanto questa opzione è applicabile unicamente quando si gestiscono le versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent precedenti a [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)].  
  
**Dominio**  
Digitare il dominio dell'utente per l'account proxy non amministratore. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] supporta più proxy, pertanto questa opzione è applicabile unicamente quando si gestiscono versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent precedenti a [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
[Implementazione di processi](../../ssms/agent/implement-jobs.md)  
  
