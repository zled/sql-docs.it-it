---
title: Annulla processi Server di Report (Management Studio) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.cancelreportserverjobs.f1
ms.assetid: 1c5b4975-49e9-4d0b-b298-2638e81edbfd
caps.latest.revision: 14
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5348146e3cce3c1f3f6288797f8a4e2bbd520cab
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="cancel-report-server-jobs-management-studio"></a>Annulla processi server di report (Management Studio)
  La finestra di dialogo **Annulla processi server di report** consente di visualizzare o annullare i report in corso. In questa finestra di dialogo vengono visualizzati tutti i processi attualmente in esecuzione nel server di report. Sebbene non sia possibile sospendere o riavviare i processi attualmente in corso di elaborazione, è possibile annullare tutti i processi o singoli processi il cui completamento sta richiedendo troppo tempo.  
  
 È possibile annullare sia i processi utente che i processi di sistema.  
  
-   Un processo utente è qualsiasi processo avviato da un singolo utente, inclusi l'esecuzione di un report su richiesta, la creazione manuale di uno snapshot della cronologia del report o la creazione manuale di uno snapshot dell'esecuzione del report. Anche una sottoscrizione standard in corso è un processo utente.  
  
-   Un processo di sistema è un processo avviato dal server di report. I processi dei sistema includono l'elaborazione pianificata dei report.  
  
 Per aprire questa pagina, avviare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connettersi a un server di report, fare clic su **Processi**e quindi su **Annulla tutti i processi**. È anche possibile aprire **Processi**, fare clic con il pulsante destro del mouse su un processo in esecuzione nel server di report e scegliere **Annulla processo/i**.  
  
 Prima di annullare un processo, è possibile visualizzare le relative proprietà per determinare quando è stato avviato. Per altre informazioni, vedere [Proprietà processo &#40;Management Studio&#41;](../../reporting-services/tools/job-properties-management-studio.md).  
  
> [!NOTE]  
>  Questa caratteristica non è supportata in [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] with Advanced Services. Questa pagina non viene visualizzata quando è in esecuzione [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)].  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Indica il nome del report. Le sottoscrizioni sono identificate tramite le rispettive descrizioni.  
  
 **Tipo**  
 I valori validi sono **Utente** e **Sistema**.  
  
 **Start Time**  
 Ora di inizio del processo.  
  
 **Nome utente**  
 Per i processi avviati da un utente, in questa colonna viene indicato il nome dell'utente.  
  
 **Stato**  
 Stato del processo. I valori validi sono **Nuovo** e **In esecuzione**. All'avvio del processo, lo stato è sempre impostato come **Nuovo** . Dopo 60 secondi, lo stato viene modificato in **In esecuzione**. Per visualizzare la modifica, è necessario aggiornare la pagina.  
  
 **OK**  
 Consente di annullare un singolo processo o più processi. I processi vengono annullati immediatamente e non possono essere ripresi. Se si annulla erroneamente un processo, è necessario richiedere di nuovo il report o la sottoscrizione per avviare un nuovo processo.  
  
## <a name="see-also"></a>Vedere anche  
 [Guida sensibile al contesto del server di report in Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Eseguire la connessione a un server di report in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Manage a Running Process](../../reporting-services/subscriptions/manage-a-running-process.md)  
  
  
