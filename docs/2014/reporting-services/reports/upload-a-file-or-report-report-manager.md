---
title: Caricare un file o un report (Gestione report) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bc1a807ed81ffb0b0aa5482d2fe3a09e70eb7908
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116181"
---
# <a name="upload-a-file-or-report-report-manager"></a>Caricare un file o un report (Gestione report)
  In Gestione report è disponibile una caratteristica di caricamento che consente di aggiungere report, modelli e altri file a un server di report senza pubblicarli da un'applicazione client. I file caricati da un file system vengono archiviati come elementi in un server di report. Il tipo di file caricato determina le modalità di archiviazione:  
  
-   I file con estensione rdl vengono archiviati come report.  
  
-   I file con estensione smdl vengono archiviati come modelli di report.  
  
-   Tutti gli altri file, ad esempio i file dell'origine dati condivisa (con estensione rds), vengono caricate come risorse. Le risorse non vengono elaborate da un server di report, ma possono essere visualizzate in Gestione report se il server di report supporta il tipo MIME del file.  
  
### <a name="to-upload-a-file-or-report"></a>Per caricare un file o un report  
  
1.  Avviare [Gestione report &#40;modalità nativa SSRS&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  In Gestione report passare alla pagina **Contenuto** . quindi passare alla cartella in cui si desidera aggiungere un elemento.  
  
3.  Fare clic su **Carica file**.  
  
4.  Fare clic su **Sfoglia** per selezionare il file da caricare. È possibile caricare un file di definizione del report, un'immagine, un documento o qualsiasi altro file che si desidera rendere disponibile nel server di report.  
  
5.  Digitare un nome per il nuovo elemento. Il nome di un elemento può includere spazi ma non i caratteri riservati, ovvero ; ? : \@ & = +, $ / * \< > |.  
  
6.  Se si desidera sostituire un elemento esistente con il nuovo elemento, selezionare **Sovrascrivi se esistente**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Creare, eliminare o modificare un'origine dati condivisa &#40;gestione Report&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Contenuto della pagina &#40;gestione Report&#41;](../contents-page-report-manager.md)   
 [Pagina Carica file &#40;Gestione report&#41;](../upload-file-page-report-manager.md)   
 [Caricare file in una cartella](../report-server/upload-files-to-a-folder.md)  
  
  
