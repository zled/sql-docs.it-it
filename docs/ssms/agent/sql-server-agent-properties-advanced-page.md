---
title: "Proprietà SQL Server Agent (pagina Avanzate) | Microsoft Docs"
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
f1_keywords: sql13.ag.agent.advanced.f1
ms.assetid: a4d798ee-4c18-40d4-b6af-63d17503738c
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7dae745a53a68ae7c0e61c64eb21d686e857c2f4
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="sql-server-agent-properties-advanced-page"></a>Proprietà SQL Server Agent (pagina Avanzate)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Usare questa pagina per visualizzare e modificare le proprietà avanzate del servizio [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Inoltro eventi SQL Server**  
Le opzioni di questa categoria consentono di attivare e configurare l'inoltro di eventi.  
  
**Inoltra eventi a un altro server**  
Gli eventi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent vengono inoltrati a un server diverso.  
  
**Server**  
Consente di selezionare il nome del server al quale inoltrare gli eventi.  
  
**Eventi non gestiti**  
Solo gli eventi non gestiti vengono inoltrati al server specificato. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent inoltra solo gli eventi ai quali non risponde alcun avviso.  
  
**Tutti gli eventi**  
Vengono inoltrati tutti gli eventi. Quando un avviso nell'istanza locale risponde a un evento, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent inoltra l'evento ed elabora l'avviso.  
  
**Eventi con gravità maggiore o uguale a**  
Vengono inoltrati solo gli eventi il cui livello di gravità e maggiore o uguale al livello specificato.  
  
**Condizione di inattività CPU**  
Le opzioni di questa categoria consentono di definire le condizioni in base alle quali [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent esegue i processi pianificati per l'esecuzione in base alla pianificazione di inattività della CPU.  
  
**Imposta condizione di inattività CPU**  
Consente di definire le condizioni in base alle quali [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent considera la CPU come inattiva.  
  
**L'utilizzo medio della CPU è inferiore al**  
La percentuale di utilizzo della CPU al di sotto della quale la CPU viene considerata inattiva.  
  
**per almeno**  
Periodo di tempo durante il quale l'utilizzo medio della CPU deve essere al di sotto del livello specificato prima che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent esegua i processi in base alla pianificazione di inattività della CPU.  
  
## <a name="see-also"></a>Vedere anche  
[Creazione e collegamento di pianificazioni ai processi](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[Gestione di eventi](../../ssms/agent/manage-events.md)  
  
