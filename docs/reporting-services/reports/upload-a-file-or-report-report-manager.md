---
title: Caricare un file o un report (Gestione report) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: reports
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: "42"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: c5934844dd9570ab95ab5641d66a465f57725e55
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="upload-a-file-or-report-report-manager"></a>Caricare un file o un report (Gestione report)
  In Gestione report è disponibile una caratteristica di caricamento che consente di aggiungere report, modelli e altri file a un server di report senza pubblicarli da un'applicazione client. I file caricati da un file system vengono archiviati come elementi in un server di report. Il tipo di file caricato determina le modalità di archiviazione:  
  
-   I file con estensione rdl vengono archiviati come report.  
  
-   I file con estensione smdl vengono archiviati come modelli di report.  
  
-   Tutti gli altri file, ad esempio i file dell'origine dati condivisa (con estensione rds), vengono caricate come risorse. Le risorse non vengono elaborate da un server di report, ma possono essere visualizzate in Gestione report se il server di report supporta il tipo MIME del file.  
  
### <a name="to-upload-a-file-or-report"></a>Per caricare un file o un report  
  
1.  Avviare [Gestione report &#40;modalità nativa SSRS&#41;](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896).  
  
2.  In Gestione report passare alla pagina **Contenuto** . quindi passare alla cartella in cui si desidera aggiungere un elemento.  
  
3.  Fare clic su **Carica file**.  
  
4.  Fare clic su **Sfoglia** per selezionare il file da caricare. È possibile caricare un file di definizione del report, un'immagine, un documento o qualsiasi altro file che si desidera rendere disponibile nel server di report.  
  
5.  Digitare un nome per il nuovo elemento. Il nome di un elemento può includere spazi ma non i caratteri riservati, ovvero ; ? : @ & = + , $ / * < > |.  
  
6.  Se si desidera sostituire un elemento esistente con il nuovo elemento, selezionare **Sovrascrivi se esistente**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Creare, eliminare o modificare un'origine dei dati condivisa &#40;Gestione report&#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Pagina Contenuto &#40;Gestione report&#41;](http://msdn.microsoft.com/library/6b16869b-158a-4934-9c85-bee934b35378)   
 [Pagina Carica file &#40;Gestione report&#41;](http://msdn.microsoft.com/library/7bb3166f-9374-4449-b66a-ffb77298507d)   
 [Caricare file in una cartella](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  
