---
title: Creare processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], creating
- SQL Server Agent jobs, creating
ms.assetid: 465fb7fc-7622-4252-a178-ea51691c935b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a6572e856d7aae3732fb45c371ec7f8c62ed335
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181141"
---
# <a name="create-jobs"></a>Crea processi
  Un processo include una serie di operazioni specificate eseguite in sequenza da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Tramite un processo è possibile eseguire un'ampia gamma di attività, inclusa l'esecuzione di script [!INCLUDE[tsql](../../includes/tsql-md.md)] , applicazioni da riga di comando, script Microsoft ActiveX, pacchetti Integration Services, comandi e query di Analysis Services o attività di replica. I processi possono eseguire attività ripetitive o pianificabili e inviare agli utenti notifiche automatiche sullo stato del processo tramite la generazione di avvisi, semplificando significativamente l'amministrazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Per creare un processo, è necessario che l'utente sia membro di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent o del ruolo predefinito del server **sysadmin** . Un processo può essere modificato solo dal proprietario o dai membri del ruolo **sysadmin** . I membri del ruolo **sysadmin** possono assegnare la proprietà di un processo ad altri utenti ed eseguire qualsiasi processo, indipendentemente dal proprietario. Per altre informazioni sui ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, vedere [Ruoli di database predefiniti di SQL Server Agent](sql-server-agent-fixed-database-roles.md).  
  
 È possibile creare processi da eseguire nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure in più istanze all'interno di un'organizzazione. Per eseguire i processi in più server, è necessario impostare almeno un server master e uno o più server di destinazione. Per altre informazioni sui server master e di destinazione, vedere [Amministrazione automatizzata in un'organizzazione](automated-administration-across-an-enterprise.md)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In Agent i dati relativi al processo e ai passaggi di processo vengono registrati nella cronologia processo.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|||  
|-|-|  
|**Descrizione**|**Argomento**|  
|Viene illustrato come creare un processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|[Creazione di un processo](create-a-job.md)|  
|Viene descritto come riassegnare la proprietà dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent a un altro utente.|[Give Others Ownership of a Job](give-others-ownership-of-a-job.md)|  
|Viene descritto come impostare il log di cronologia processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.|[Set Up the Job History Log](set-up-the-job-history-log.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire passaggi di processo](manage-job-steps.md)   
 [Amministrazione automatizzata in un'organizzazione](automated-administration-across-an-enterprise.md)   
 [Creare e collegare pianificazioni ai processi](create-and-attach-schedules-to-jobs.md)   
 [Eseguire i processi](run-jobs.md)   
 [Visualizzare o modificare processi](view-or-modify-jobs.md)  
  
  
