---
title: "Limitare la cronologia dei report (Gestione report) | Microsoft Docs"
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
  - "visualizzazione della cronologia del report"
  - "cronologia del report [Reporting Services], visualizzazione cronologia"
  - "cronologia del report [Reporting Services], configurazione cronologia"
  - "dati della cronologia [Reporting Services]"
  - "visualizzazione della cronologia del report"
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
caps.latest.revision: 36
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 36
---
# Limitare la cronologia dei report (Gestione report)
  La cronologia di un report è una raccolta di snapshot del report creati nel tempo. È possibile creare la cronologia del report su richiesta o pianificare la frequenza di creazione di uno snapshot e della relativa aggiunta alla cronologia.  
  
 La cronologia del report viene archiviata nel database del server di report. Se gli snapshot del report contengono una quantità di dati elevata, è possibile limitare la cronologia del report per minimizzare l'impatto della memorizzazione degli snapshot sulle dimensione del database.  
  
### Per configurare la cronologia del report per un server di report  
  
1.  In Gestione report fare clic su **Impostazioni sito** sulla barra degli strumenti principale.  
  
2.  Selezionare **Nessun limite per il numero di snapshot archiviabili nella cronologia** se si desidera mantenere tutta la cronologia del report per un periodo illimitato. In alternativa, selezionare **Numero massimo di copie della cronologia** per specificare il numero massimo di snapshot che è possibile mantenere per qualsiasi report.  
  
3.  Fare clic su **Applica**.  
  
### Per configurare la cronologia per un report specifico  
  
1.  In Gestione report passare al report per il quale si desidera configurare la cronologia e quindi fare clic su di esso per aprirlo.  
  
2.  Fare clic sulla scheda **Proprietà**.  
  
3.  Fare clic sulla scheda **Cronologia**.  
  
4.  Selezionare le opzioni per il report e fare clic su **Applica**. Per informazioni dettagliate su ogni opzione, vedere [Pagina delle proprietà Opzioni snapshot &#40;Gestione report&#41;](../Topic/Snapshot%20Options%20Properties%20Page%20\(Report%20Manager\).md).  
  
## Vedere anche  
 [Aggiungere uno snapshot alla cronologia del report &#40;Gestione report&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Gestione report &#40;modalità nativa SSRS&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)  
  
  