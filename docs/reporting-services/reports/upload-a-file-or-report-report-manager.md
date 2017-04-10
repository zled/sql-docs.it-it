---
title: "Caricare un file o un report (Gestione report) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pubblicazione di report [Reporting Services], caricamento di file"
  - "report [Reporting Services], pubblicazione"
  - "caricamento di report [Reporting Services]"
  - "caricamento di file [Reporting Services]"
  - "file [Reporting Services], caricamento"
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
caps.latest.revision: 42
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 42
---
# Caricare un file o un report (Gestione report)
  In Gestione report è disponibile una caratteristica di caricamento che consente di aggiungere report, modelli e altri file a un server di report senza pubblicarli da un'applicazione client. I file caricati da un file system vengono archiviati come elementi in un server di report. Il tipo di file caricato determina le modalità di archiviazione:  
  
-   I file con estensione rdl vengono archiviati come report.  
  
-   I file con estensione smdl vengono archiviati come modelli di report.  
  
-   Tutti gli altri file, ad esempio i file dell'origine dati condivisa (con estensione rds), vengono caricate come risorse. Le risorse non vengono elaborate da un server di report, ma possono essere visualizzate in Gestione report se il server di report supporta il tipo MIME del file.  
  
### Per caricare un file o un report  
  
1.  Avviare [Gestione Report &#40;modalità nativa SSRS&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  In Gestione report passare alla pagina **Contenuto**. quindi passare alla cartella in cui si desidera aggiungere un elemento.  
  
3.  Fare clic su **Carica file**.  
  
4.  Fare clic su **Sfoglia** per selezionare il file da caricare. È possibile caricare un file di definizione del report, un'immagine, un documento o qualsiasi altro file che si desidera rendere disponibile nel server di report.  
  
5.  Digitare un nome per il nuovo elemento. Il nome di un elemento può includere spazi ma non i caratteri riservati, ovvero ; ? : @ & = + , $ / * \< > |.  
  
6.  Se si desidera sostituire un elemento esistente con il nuovo elemento, selezionare **Sovrascrivi se esistente**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## Vedere anche  
 [Creare, eliminare o modificare un'origine dei dati condivisa &#40;Gestione report&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [Pagina Contenuto &#40;Gestione report&#41;](../Topic/Contents%20Page%20\(Report%20Manager\).md)   
 [Pagina Carica file &#40;Gestione report&#41;](../Topic/Upload%20File%20Page%20\(Report%20Manager\).md)   
 [Caricare file in una cartella](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  