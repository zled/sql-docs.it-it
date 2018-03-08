---
title: Associare un report o un modello a un'origine dati condivisa (SSRS) | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-data
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shared data sources [Reporting Services]
- data sources [Reporting Services], shared
ms.assetid: 23cc15f2-2883-48e2-bc6c-fa0ab61a2e21
caps.latest.revision: "11"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 44809cf12df1fac42a99882672fa945800a9f5f4
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="bind-a-report-or-model-to-a-shared-data-source-ssrs"></a>Associare un report o un modello a un'origine dati condivisa (SSRS)
  In alcune situazioni, ad esempio quando si sposta un report o un modello da un server di test a uno di produzione, potrebbe essere necessario salvare il file nel computer locale e quindi caricarlo in un altro server di report. Quando si carica il report o il modello nel nuovo server, è necessario riassociarlo a un'origine dei dati condivisa archiviata nel nuovo server di report. Se il report o il modello non viene riassociato, non funzionerà correttamente quando vi si accede dal nuovo server di report.  
  
> [!IMPORTANT]  
>  Per poter riassociare un report o un modello a un'origine dei dati condivisa, quest'ultima deve esistere già nel server di report o nella raccolta di SharePoint. Per altre informazioni sulle origini dati, vedere [Creare, modificare ed eliminare origini dati condivise &#40;SSRS&#41;](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md).  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-native-mode"></a>Per associare un report o un modello a un'origine dei dati condivisa in un server di report in esecuzione in modalità nativa  
  
1.  In **Gestione report**fare clic sul nome del report o del modello caricato nel server.  
  
     Verrà aperta la scheda Proprietà.  
  
2.  Fare clic su **Origini dati**.  
  
3.  Fare clic su **Sfoglia**e quindi individuare l'origine dati a cui si vuole associare il report o il modello.  
  
4.  Selezionare l'origine dati e quindi fare clic su **OK**.  
  
5.  Fare clic su **Applica**.  
  
     Il report o il modello verrà quindi associato all'origine dei dati selezionata.  
  
### <a name="to-bind-a-report-or-model-to-a-shared-data-source-on-a-report-server-running-in-sharepoint-integrated-mode"></a>Per associare un report o un modello a un'origine dei dati condivisa in un server di report in esecuzione in modalità integrata SharePoint  
  
1.  Se la raccolta non è già aperta, fare clic sul suo nome sulla barra di avvio veloce. Se il nome della raccolta non è visualizzato, fare clic su **Visualizza tutto il contenuto del sito**e quindi sul nome della raccolta desiderata.  
  
2.  Selezionare il report o il modello e fare clic sulla freccia verso il basso.  
  
3.  Fare clic su **Gestisci origini dati**.  
  
4.  Fare clic su **dataSource1**.  
  
5.  Nell'area **Tipo di connessione** verificare che **Origine dati condivisa** sia selezionata.  
  
6.  Nell'area **Collegamento origine dati** fare clic sul pulsante con i puntini di sospensione.  
  
7.  Individuare l'origine dei dati da utilizzare.  
  
8.  Selezionare l'origine dati e fare clic su **OK**.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
10. Scegliere **Chiudi**.  
  
## <a name="see-also"></a>Vedere anche  
 [Caricare un file o un report &#40;Gestione report&#41;](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)   
 [Caricare documenti in una raccolta di SharePoint &#40;Reporting Services in modalità SharePoint&#41;](../../reporting-services/report-server-sharepoint/upload-documents-to-a-sharepoint-library-reporting-services-in-sharepoint-mode.md)   
 [Creare e gestire origini dati condivise &#40;Reporting Services in modalità integrata SharePoint&#41;](http://msdn.microsoft.com/library/2d3428e4-a810-4e66-a287-ff18e57fad76)   
 [Creare, eliminare o modificare un'origine dei dati condivisa &#40;Gestione report&#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Connessioni dati, origini dati e stringhe di connessione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Origini dei dati supportate da Reporting Services &#40;SSRS&#41;](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)  
  
  
