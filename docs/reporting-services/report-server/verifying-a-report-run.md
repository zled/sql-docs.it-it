---
title: "Verifica dell&#39;esecuzione di un report | Microsoft Docs"
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
  - "controllo [Reporting Services]"
  - "verifica dell'esecuzione di report"
  - "log [Reporting Services], verifica dell'esecuzione di report"
  - "dati di esecuzione di report [Reporting Services]"
  - "status information [Reporting Services]"
  - "elaborazione di report [Reporting Services], verifica dell'esecuzione"
  - "controllo dell'esecuzione di report"
ms.assetid: 18a98f2f-6b40-454e-9b37-568ed1a96458
caps.latest.revision: 37
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 37
---
# Verifica dell&#39;esecuzione di un report
  Per visualizzare informazioni sullo stato di elaborazione di un report, è possibile utilizzare i file di log oppure controllare le informazioni sullo stato visualizzate con il report in Gestione report.  
  
## Origini dei dati per l'esecuzione del report  
 I log di esecuzione di un report contengono tutte le informazioni sull'esecuzione del report, tra cui il nome del report, il nome dell'utente che lo ha eseguito, la data e l'ora di esecuzione e l'estensione per il recapito utilizzata per distribuire il report. Per visualizzare e analizzare questi dati, è possibile copiare il log di esecuzione del report in tabelle di database, in modo che sia più semplice eseguire query e creare report sui dati di esecuzione.  
  
 I file di log contengono numerose voci sull'esecuzione dei report e su altre attività del server. Dato che i file di log contengono una così grande quantità di dati, è consigliabile utilizzare Gestione report se si desidera verificare unicamente quando è avvenuta l'ultima esecuzione del report. Se sono necessarie informazioni aggiuntive, è necessario visualizzare i file di log.  
  
> [!NOTE]  
>  In Gestione report non vengono visualizzate la data e l'ora di elaborazione dei report eseguiti su richiesta.  
  
 Nella tabella seguente viene descritto come visualizzare la data e l'ora di elaborazione per vari tipi di report.  
  
|Tipo di report|Posizione delle informazioni sulla data e l'ora|Operazioni da eseguire per visualizzare le informazioni|  
|-----------------------------|-----------------------------------------------|-----------------------------------------------|  
|Report che viene eseguito come snapshot del report|Pagina Contenuto. Per altre informazioni, vedere [Pagina Contenuto &#40;Gestione report&#41;](../Topic/Contents%20Page%20\(Report%20Manager\).md).|1) Individuare la cartella che contiene il report.<br /><br /> 2) Impostare la visualizzazione Dettagli per la cartella.<br /><br /> 3) Osservare data e ora nella colonna **Data ultima esecuzione**.|  
|Snapshot della cronologia del report|Pagina delle proprietà Cronologia. Per altre informazioni, vedere [Pagina delle proprietà Opzioni snapshot &#40;Gestione report&#41;](../Topic/Snapshot%20Options%20Properties%20Page%20\(Report%20Manager\).md).|1) Aprire il report.<br /><br /> 2) Fare clic sulla pagina **Proprietà**.<br /><br /> 3) Fare clic sulla scheda **Cronologia**.<br /><br /> 4) Osservare data e ora nella colonna **Data ultima esecuzione**.|  
|Report memorizzato nella cache|Pianificazione utilizzata per creare e aggiornare il report memorizzato nella cache.|1) Aprire il report.<br /><br /> 2) Fare clic sulla pagina **Proprietà**.<br /><br /> 3) Fare clic sulla scheda **Esecuzione**.<br /><br /> 4) Aprire la pianificazione.|  
  
## Vedere anche  
 [File di log e origini di Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [Impostare proprietà di elaborazione dei report](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Gestione report &#40;modalità nativa SSRS&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)  
  
  