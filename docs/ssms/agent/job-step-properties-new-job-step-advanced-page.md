---
title: "Proprietà passaggio processo - Nuovo passaggio di processo (pagina Avanzate) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.ag.job.stepadvanced.f1
ms.assetid: bdecfd4f-bcd8-4ba2-8ada-fbb636314f40
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6ad17a4381de9bac0443cd0bc65ebfbfbd1f9a2e
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="job-step-properties---new-job-step-advanced-page"></a>Proprietà passaggio processo - Nuovo passaggio di processo (pagina Avanzate)
Usare questa pagina per visualizzare e modificare le proprietà di un passaggio di processo di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Azione in caso di esito positivo**  
Consente di impostare l'azione che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent deve eseguire in caso di esito positivo del passaggio di processo.  
  
**Numero tentativi**  
Consente di impostare il numero di tentativi eseguiti da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent per ripetere un passaggio di processo non riuscito.  
  
**Intervallo tra i tentativi (minuti)**  
Consente di impostare l'intervallo di attesa di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent tra l'esecuzione di un tentativo e l'altro.  
  
**Azione in caso di esito negativo**  
Consente di impostare l'azione che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent deve eseguire in caso di esito negativo del passaggio di processo.  
  
## <a name="options-for-transact-sql-job-steps"></a>Opzioni per i passaggi del processo Transact-SQL  
**File di output**  
Consente di impostare il file da utilizzare per l'output del passaggio di processo. Questa opzione è disponibile solo per i membri del ruolo predefinito del server **sysadmin** .  
  
**...**  
Selezionare il file da utilizzare per l'output del passaggio di processo.  
  
**Visualizza**  
In [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], questo pulsante è disabilitato per la visualizzazione di file di output. In alternativa, utilizzare Notepad per visualizzare i file di output del passaggio di processo.  
  
**Accoda output a file esistente**  
Consente di accodare l'output al contenuto già esistente nel file. Diversamente, il precedente contenuto del file viene sovrascritto ogni volta che il passaggio di processo viene eseguito.  
  
**Registra nella tabella**  
Consente di registrare l'output del passaggio di processo nella tabella **sysjobstepslogs** del database **msdb** .  
  
**Visualizza**  
Dopo avere eseguito almeno una volta il passaggio di processo, fare clic su **Visualizza** per visualizzare l'output corrispondente nella tabella.  
  
**Accoda output a voce esistente nella tabella**  
Consente di accodare l'output al contenuto già esistente nella tabella. Diversamente, il precedente contenuto della tabella viene sovrascritto ogni volta che il passaggio di processo viene eseguito.  
  
**Includi output passaggio nella cronologia**  
Selezionare questa opzione per includere l'output del passaggio di processo nella cronologia processo.  
  
**Esegui come utente**  
Se si è membri del ruolo predefinito del server **sysadmin** , è possibile selezionare un altro account di accesso SQL per eseguire questo passaggio di processo.  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a>Opzioni per i passaggi del processo Sistema operativo (CmdExec)  
**File di output**  
Consente di impostare il file da utilizzare per l'output del passaggio di processo.  
  
**...**  
Selezionare il file da utilizzare per l'output del passaggio di processo.  
  
**Visualizza**  
In [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], questo pulsante è disabilitato per la visualizzazione di file di output. In alternativa, utilizzare Notepad per visualizzare i file di output del passaggio di processo.  
  
**Accoda output a file esistente**  
Consente di accordare l'output del passaggio di processo al precedente contenuto del file ogni volta che il passaggio di processo viene eseguito.  
  
**Registra nella tabella**  
Consente di registrare l'output del passaggio di processo nella tabella **sysjobstepslogs** del database **msdb** .  
  
**Visualizza**  
Dopo avere eseguito almeno una volta il passaggio di processo, fare clic su **Visualizza** per visualizzare l'output corrispondente nella tabella.  
  
**Accoda output a voce esistente nella tabella**  
Consente di accodare l'output al contenuto già esistente nella tabella. Diversamente, il precedente contenuto della tabella viene sovrascritto ogni volta che il passaggio di processo viene eseguito.  
  
**Includi output passaggio nella cronologia**  
Selezionare questa opzione per includere l'output del passaggio di processo nella cronologia processo.  
  
## <a name="options-for-powershell-job-steps"></a>Opzioni per i passaggi di processo di PowerShell  
**File di output**  
Consente di impostare il file da utilizzare per l'output del passaggio di processo.  
  
**...**  
Selezionare il file da utilizzare per l'output del passaggio di processo.  
  
**Visualizza**  
In [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], questo pulsante è disabilitato per la visualizzazione di file di output. In alternativa, utilizzare Notepad per visualizzare i file di output del passaggio di processo.  
  
**Accoda output a file esistente**  
Consente di accordare l'output del passaggio di processo al precedente contenuto del file ogni volta che il passaggio di processo viene eseguito.  
  
**Registra nella tabella**  
Consente di registrare l'output del passaggio di processo nella tabella **sysjobstepslogs** del database **msdb** .  
  
**Visualizza**  
Dopo avere eseguito almeno una volta il passaggio di processo, fare clic su **Visualizza** per visualizzare l'output corrispondente nella tabella.  
  
**Accoda output a voce esistente nella tabella**  
Consente di accodare l'output al contenuto già esistente nella tabella. Diversamente, il precedente contenuto della tabella viene sovrascritto ogni volta che il passaggio di processo viene eseguito.  
  
**Includi output passaggio nella cronologia**  
Selezionare questa opzione per includere l'output del passaggio di processo nella cronologia processo.  
  
## <a name="options-for-replication-queue-reader-job-steps"></a>Opzioni per i passaggi del processo Lettura coda repliche  
**Server**  
Consente di impostare il server da utilizzare per un passaggio di processo Lettura coda repliche.  
  
**Database**  
Consente di impostare il database da utilizzare per un passaggio di processo Lettura coda repliche.  
  
## <a name="options-for-sql-server-analysis-services-job-steps"></a>Opzioni per i passaggi del processo SQL Server Analysis Services  
**File di output**  
Consente di impostare il file da utilizzare per l'output del passaggio di processo. Questa opzione è disponibile solo per i membri del ruolo predefinito del server **sysadmin** .  
  
**...**  
Selezionare il file da utilizzare per l'output del passaggio di processo.  
  
**Visualizza**  
In [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)], questo pulsante è disabilitato per la visualizzazione di file di output. In alternativa, utilizzare Notepad per visualizzare i file di output del passaggio di processo.  
  
**Accoda output a file esistente**  
Consente di accodare l'output al contenuto già esistente nel file. Diversamente, il precedente contenuto del file viene sovrascritto ogni volta che il passaggio di processo viene eseguito.  
  
**Registra nella tabella**  
Consente di registrare l'output del passaggio di processo nella tabella **sysjobstepslogs** del database **msdb** .  
  
**Visualizza**  
Dopo avere eseguito almeno una volta il passaggio di processo, fare clic su **Visualizza** per visualizzare l'output corrispondente nella tabella.  
  
**Accoda output a voce esistente nella tabella**  
Consente di accodare l'output al contenuto già esistente nella tabella. Diversamente, il precedente contenuto della tabella viene sovrascritto ogni volta che il passaggio di processo viene eseguito.  
  
**Includi output passaggio nella cronologia**  
Selezionare questa opzione per includere l'output del passaggio di processo nella cronologia processo.  
  
## <a name="see-also"></a>Vedere anche  
[Gestire passaggi di processo](../../ssms/agent/manage-job-steps.md)  
  
