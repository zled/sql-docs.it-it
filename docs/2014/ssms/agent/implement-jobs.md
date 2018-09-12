---
title: Implementare processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 376669247512c48b21aca1600151c1dac5d6e2f3
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43818877"
---
# <a name="implement-jobs"></a>Implementazione di processi
  I processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent consentono di automatizzare le attività amministrative di routine, in modo da rendere più efficiente l'amministrazione.  
  
 Un processo include una serie di operazioni specificate eseguite in sequenza da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Un processo può eseguire un'ampia gamma di attività, inclusa l'esecuzione di script [!INCLUDE[tsql](../../includes/tsql-md.md)] , applicazioni della riga di comando, script Microsoft ActiveX, pacchetti di Integration Services, comandi e query di Analysis Services o attività di replica. I processi possono eseguire attività ripetitive o pianificabili e possono inviare automaticamente agli utenti notifiche sullo stato dei processi tramite la generazione di avvisi, semplificando notevolmente l'amministrazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 È possibile eseguire un processo manualmente oppure configurarlo per l'esecuzione in base a una pianificazione o in risposta ad avvisi.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|||  
|-|-|  
|**Descrizione**|**Argomento**|  
|Contiene informazioni sulla creazione dei processi e sull'assegnazione della proprietà.|[Crea processi](create-jobs.md)|  
|Contiene informazioni sull'organizzazione dei processi in categorie.|[Organizzare processi](organize-jobs.md)|  
|Contiene informazioni sui diversi tipi di passaggi di processo che è possibile creare e sulla rispettiva modalità di gestione.|[Gestire passaggi di processo](manage-job-steps.md)|  
|Contiene informazioni sulla definizione del momento di avvio dei processi e sulla relativa frequenza di esecuzione.|[Creazione e collegamento di pianificazioni ai processi](create-and-attach-schedules-to-jobs.md)|  
|Sono incluse informazioni sull'esecuzione manuale dei processi (senza pianificazione).|[Esecuzione di processi](run-jobs.md)|  
|Sono incluse informazioni sulla configurazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per rispondere ai processi. È possibile configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, ad esempio, in modo da notificare agli amministratori il completamento dei processi.|[Specifica delle risposte ai processi](specify-job-responses.md)|  
|Contiene informazioni sulla visualizzazione dei processi esistenti e sulla cronologia processo eseguiti, nonché sulle modalità di modifica dei processi.|[Visualizzare o modificare processi](view-or-modify-jobs.md)|  
|Contiene informazioni sulla modalità di eliminazione dei processi.|[Eliminare processi](delete-jobs.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione della sicurezza di SQL Server Agent](implement-sql-server-agent-security.md)  
  
  
