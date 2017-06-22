---
title: Implementare processi | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 30b61e4aa32828763d4531c53cb7f308a926798b
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="implement-jobs"></a>Implementazione di processi
I processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent consentono di automatizzare le attività amministrative di routine, in modo da rendere più efficiente l'amministrazione.  
  
Un processo include una serie di operazioni specificate eseguite in sequenza da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent. Un processo può eseguire un'ampia gamma di attività, inclusa l'esecuzione di script [!INCLUDE[tsql](../../includes/tsql_md.md)] , applicazioni della riga di comando, script Microsoft ActiveX, pacchetti di Integration Services, comandi e query di Analysis Services o attività di replica. I processi possono eseguire attività ripetitive o pianificabili e possono inviare automaticamente agli utenti notifiche sullo stato dei processi tramite la generazione di avvisi, semplificando notevolmente l'amministrazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] .  
  
È possibile eseguire un processo manualmente oppure configurarlo per l'esecuzione in base a una pianificazione o in risposta ad avvisi.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|||  
|-|-|  
|**Description**|**Argomento**|  
|Contiene informazioni sulla creazione dei processi e sull'assegnazione della proprietà.|[Crea processi](../../ssms/agent/create-jobs.md)|  
|Contiene informazioni sull'organizzazione dei processi in categorie.|[Organizzare processi](../../ssms/agent/organize-jobs.md)|  
|Contiene informazioni sui diversi tipi di passaggi di processo che è possibile creare e sulla rispettiva modalità di gestione.|[Gestire passaggi di processo](../../ssms/agent/manage-job-steps.md)|  
|Contiene informazioni sulla definizione del momento di avvio dei processi e sulla relativa frequenza di esecuzione.|[Creazione e collegamento di pianificazioni ai processi](../../ssms/agent/create-and-attach-schedules-to-jobs.md)|  
|Sono incluse informazioni sull'esecuzione manuale dei processi (senza pianificazione).|[Esecuzione di processi](../../ssms/agent/run-jobs.md)|  
|Sono incluse informazioni sulla configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent per rispondere ai processi. È possibile configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, ad esempio, in modo da notificare agli amministratori il completamento dei processi.|[Specifica delle risposte ai processi](../../ssms/agent/specify-job-responses.md)|  
|Contiene informazioni sulla visualizzazione dei processi esistenti e sulla cronologia processo eseguiti, nonché sulle modalità di modifica dei processi.|[Visualizzare o modificare processi](../../ssms/agent/view-or-modify-jobs.md)|  
|Contiene informazioni sulla modalità di eliminazione dei processi.|[Eliminare processi](../../ssms/agent/delete-jobs.md)|  
  
## <a name="see-also"></a>Vedere anche  
[Implementazione della sicurezza di SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md)  
  

