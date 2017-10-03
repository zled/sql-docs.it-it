---
title: Utilizzando il report (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: 49c3c1da-b106-41f6-9173-16ff225bade8
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: fc31861f7eef73a2ddb88faa4aa59b1bf289d2ea
ms.contentlocale: it-it
ms.lasthandoff: 09/27/2017

---
# <a name="using-my-reports-report-builder-and-ssrs"></a>Utilizzo della cartella Report personali (Generatore report e SSRS)
  In un server di report configurato in modalità nativa, la cartella Report personali è un'area di lavoro personale che è possibile utilizzare per archiviare e gestire i report di cui si è proprietari. Le altre cartelle del server di report sono pubbliche e in genere è necessario disporre di autorizzazioni avanzate per aggiungere o modificare contenuto in tali cartelle. Al contrario, la cartella Report personali è un'area di lavoro gestita dall'utente nella quale è possibile aggiungere o rimuovere report o cartelle e salvare report collegati con impostazioni personalizzate.  
  
 Concettualmente, la cartella Report personali è simile alla cartella Documenti del file system di Windows. Nonostante ogni utente sia proprietario di una cartella Report personali, la cartella di ciascuno è diversa da quelle di tutti gli altri utenti. L'accesso alla cartella Report personali di un determinato utente è consentito solo all'utente stesso e agli amministratori del server di report.  
  
 La caratteristica funzionalità Report personali è facoltativa e può essere disabilitata da un amministratore del server di report. Se è abilitata, viene visualizzata una cartella Report personali nella cartella Home, alla quale è possibile accedere tramite Gestione report o un Web browser. Per ulteriori informazioni, vedere [ricerca e visualizzazione dei report in Gestione Report &#40; Generatore report e SSRS &#41; ](finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs.md).  
  
 In un server di report configurato nella modalità integrata SharePoint, non esiste una cartella Report personali equivalente. Per altre informazioni, vedere [Ricerca, visualizzazione e gestione dei report &#40;Generatore report SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="ways-to-use-my-reports"></a>Modalità di utilizzo della funzionalità Report personali  
 Quando viene creata, la cartella Report personali è vuota. In seguito, è possibile aggiungervi report, cartelle e altri elementi. Di seguito vengono indicate alcune delle possibili modalità di aggiunta di contenuto alla cartella Report personali.  
  
-   Creare un report collegato personale e archiviarlo nella cartella Report personali. Non tutti i report possono essere collegati. Per altre informazioni, vedere [Creare un report collegato](../../reporting-services/reports/create-a-linked-report.md).  
  
-   Caricare un file di definizione del report (estensione rdl), un file di modello del report (estensione smdl) o altri file dal file system. È possibile caricare qualsiasi tipo di file, che verranno tuttavia elaborati dal server di report solo i file di report dispongono dell'estensione rdl o smdl. Per ulteriori informazioni, vedere le definizioni dei Report"nella [documentazione relativa a Reporting Services](http://go.microsoft.com/fwlink/?linkid=121312) nella documentazione Online di SQL Server e [caricare un File o un Report &#40; Gestione report &#41; ](../../reporting-services/reports/upload-a-file-or-report-report-manager.md).  
  
-   Creare e pubblicare i report personali nella cartella Report personali. Per ulteriori informazioni, vedere [visualizzazione di progettazione di Report &#40; Generatore report &#41; ](../../reporting-services/report-builder/report-design-view-report-builder.md).  
  
 Le autorizzazioni per la cartella Report personali, in genere, consentono al proprietario di gestire la cartella stessa. Tuttavia, è l'amministratore del server di report che decide quali attività possono essere eseguite dagli utenti. Se non si dispone di autorizzazioni sufficienti per utilizzare la cartella Report personali, rivolgersi all'amministratore del server di report.  
  
## <a name="searching-my-reports"></a>Ricerche nella cartella Report personali  
 Quando un utente esegue una ricerca in un database del server di report, tra i contenuti in cui viene eseguita la ricerca vengono inclusi quelli della cartella Report personali dell'utente mentre sono esclusi quelli delle cartelle Report personali degli altri utenti. Nell'elenco dei risultati della ricerca vengono inclusi solo i report a cui l'utente che ha eseguito la ricerca è autorizzato ad accedere.  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca, visualizzazione e gestione dei report &#40;Generatore report SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
