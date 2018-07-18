---
title: Sospendere e riprendere le pianificazioni condivise | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pausing schedules
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services], resuming
- resuming schedules
- continuing schedules
- schedules [Reporting Services], resuming
- schedules [Reporting Services], pausing
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 68971d1dfd25f7e2e15be0007e1aaf5efb19099f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063258"
---
# <a name="pause-and-resume-shared-schedules"></a>Pause and Resume Shared Schedules
  È possibile sospendere e quindi riprendere una pianificazione condivisa attualmente in uso. In genere, si sospende una pianificazione condivisa per bloccare temporaneamente una pianificazione che viene utilizzata per attivare sottoscrizioni e operazioni di elaborazione di report. Solo le pianificazioni condivise possono essere sospese e riprese. Non è possibile sospendere le pianificazioni specifiche dei report.  
  
 Non è possibile sospendere e riprendere le operazioni di elaborazione dei report in corso. È possibile sospendere e riprendere esclusivamente le pianificazioni presenti nella coda del servizio SQL Server Agent. Un processo in corso è esterno all'ambito del motore di pianificazione. Per altre informazioni, vedere [gestire un processo in esecuzione](manage-a-running-process.md)  
  
 Mentre una pianificazione condivisa è in sospeso, tutte le operazioni che dovevano essere eseguite in tale intervallo di tempo possono essere ignorate. Quando una pianificazione condivisa viene ripresa, le operazioni di elaborazione dei report e delle sottoscrizioni vengono eseguite in corrispondenza del successivo orario pianificato, utilizzando come riferimento l'ora locale del server di report. Tramite le applicazioni di servizio SharePoint o il server di report in modalità nativa non vengono eseguite le operazioni pianificate che sarebbero state eseguite se la pianificazione non fosse stata sospesa.  
  
 Contenuto dell'argomento:  
  
-   [Sospendere e riprendere le pianificazioni condivise (modalità nativa)](#bkmk_native)  
  
-   [Sospendere e riprendere le pianificazioni condivise (modalità SharePoint)](#bkmk_sharepoint)  
  
##  <a name="bkmk_native"></a> Sospendere e riprendere le pianificazioni condivise (modalità nativa)  
 Per sospendere e riprendere una pianificazione condivisa, utilizzare la pagina Pianificazioni in Gestione report. Non è possibile utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]poiché non dispone delle opzioni di sospensione e ripresa delle pianificazioni. Per altre informazioni, vedere [crea, modifica ed eliminare pianificazioni](create-modify-and-delete-schedules.md).  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a>Per sospendere o riprendere una pianificazione condivisa  
  
1.  Da Gestione report fare clic su **Impostazioni sito**.  
  
2.  Fare clic su **Pianificazioni**.  
  
3.  Selezionare la pianificazione e fare clic su **Sospendi** o **Riprendi** nella barra multifunzione. Se una pianificazione è attualmente sospesa, nella colonna **Stato** verrà visualizzato **Sospeso**.  
  
##  <a name="bkmk_sharepoint"></a> Sospendere e riprendere le pianificazioni condivise (modalità SharePoint)  
 Per sospende e riprendere una pianificazione condivisa, utilizzare la pagina Impostazioni sito o PowerShell. Le pianificazioni sono gestite per sito di SharePoint.  
  
#### <a name="to-pause-or-resume-a-shared-schedule"></a>Per sospendere o riprendere una pianificazione condivisa  
  
1.  Fare clic su **Azioni sito**.  
  
2.  Fare clic su **Impostazioni sito**.  
  
3.  Nella sezione Reporting Services fare clic su **Gestisci pianificazioni condivise**.  
  
4.  Selezionare la pianificazione e fare clic su **Sospendi pianificazioni selezionate** o **Esegui pianificazioni selezionate**. Se una pianificazione è attualmente sospesa, nella colonna **Stato** verrà visualizzato **Sospeso**.  
  
## <a name="see-also"></a>Vedere anche  
 [Pianificazioni](schedules.md)   
 [Create, Modify, and Delete Schedules](create-modify-and-delete-schedules.md)   
 [Modificare i fusi orari e le impostazioni dell'orologio in un server di report](change-time-zones-and-clock-settings-on-a-report-server.md)   
 [Gestire un processo in esecuzione](manage-a-running-process.md)  
  
  