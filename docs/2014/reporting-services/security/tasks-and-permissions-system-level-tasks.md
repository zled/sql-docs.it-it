---
title: Attività a livello di sistema | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 284349672feca872e8f9b704314ae070ec687df7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37229001"
---
# <a name="system-level-tasks"></a>Attività a livello di sistema
  Un'attività a livello di sistema è una raccolta di autorizzazioni correlate alle operazioni eseguibili per l'intero sito del server di report. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] include anche attività a livello di elemento applicabili a elementi specifici. Per altre informazioni, vedere [Attività a livello di elemento](tasks-and-permissions-item-level-tasks.md). Per altre informazioni sulle attività e le autorizzazioni in generale, vedere [attività e autorizzazioni](tasks-and-permissions.md).  
  
> [!NOTE]  
>  Se si gestiscono queste attività a livello di programmazione, è necessario utilizzare metodi che supportano attività a livello di sistema. Per altre informazioni, vedere <xref:ReportService2010.ReportingService2010.ListTasks%2A> e <xref:ReportService2010.ReportingService2010.ListRoles%2A>.  
  
## <a name="permissions-in-system-level-tasks"></a>Autorizzazioni nelle attività a livello di sistema  
 Nella tabella seguente vengono indicate le autorizzazioni per ogni attività a livello di sistema. L'elenco delle autorizzazioni è puramente informativo e ha lo scopo di fornire una descrizione precisa delle funzionalità disponibili tramite ogni attività.  
  
|Attività|Autorizzazioni|  
|----------|-----------------|  
|Esecuzione delle definizioni dei report|Esecuzione delle definizioni dei report (il nome dell'autorizzazione e il nome dell'attività sono identici)|  
|Generazione di eventi|Generazione di eventi|  
|Gestisci processi|Lettura delle proprietà di sistema<br /><br /> Aggiornamento delle proprietà di sistema|  
|Gestione delle proprietà del server di report|Lettura delle proprietà di sistema<br /><br /> Aggiornamento delle proprietà di sistema|  
|Gestione di ruoli|Creazione di ruoli<br /><br /> Eliminazione di ruoli<br /><br /> Lettura delle proprietà di ruolo<br /><br /> Aggiornamento delle proprietà di ruolo|  
|Gestione di pianificazioni condivise|Creazione di pianificazioni|  
|Gestione della sicurezza del server di report|Lettura dei criteri di sicurezza del sistema<br /><br /> Aggiornamento dei criteri di sicurezza del sistema|  
|Visualizzazione delle proprietà del server di report|Lettura delle proprietà di sistema|  
|Visualizzazione di pianificazioni condivise|Lettura di pianificazioni|  
  
## <a name="see-also"></a>Vedere anche  
 [Concessione di autorizzazioni in un server di report in modalità nativa](granting-permissions-on-a-native-mode-report-server.md)  
  
  
