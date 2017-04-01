---
title: "Avviare Generatore report | Microsoft Docs"
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
  - "Generatore report, avvio"
  - "avvio di Generatore report"
  - "integrazione con SharePoint [Reporting Services], avvio di Generatore report"
  - "avvio di Generatore report"
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
caps.latest.revision: 56
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 56
---
# Avviare Generatore report
  Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] è un ambiente di creazione di report autonomo. Permette di creare report impaginati e di pubblicarli in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installato in modalità nativa o nella modalità integrata SharePoint.  
  
 La prima volta che si avvia [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] dal portale Web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] o [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in modalità integrata SharePoint, viene richiesto di scaricarlo dall'Area download Microsoft. 
 
![report-builder-get-report-builder](../../reporting-services/report-builder/media/report-builder-get-report-builder.png) 
 
 L'utente o un amministratore può anche [installare Generatore report nel computer dall'Area download Microsoft](http://go.microsoft.com/fwlink/?LinkID=219138). Per altri dettagli, vedere "Installare Generatore report con Systems Manager Server" in [Installare Generatore Report](../../reporting-services/install-windows/install-report-builder.md).
 
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] non viene installato quando si installa [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]; è necessario scaricarlo e installarlo separatamente.  
  
 Quando si avvia [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] dal portale Web o dal sito di SharePoint, se si apre una versione precedente di [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] , contattare l'amministratore, che può aggiornare la versione sul portale Web o sul sito di SharePoint.  
  
## Per avviare [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] dal portale Web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
1.  Digitare l'URL per il server di report nella barra degli indirizzi del browser. L'URL predefinito è http://\<*nomeserver*>/reports.  
  
2.  Nella barra superiore del portale Web, selezionare **Nuovo** > **Report impaginato**.  
  
     ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png "PBI_SSMRP_NewMenu")  
  
     La prima volta viene richiesto di [installare Generatore Report](../../reporting-services/install-windows/install-report-builder.md). 
  
     In seguito, viene aperto [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] ed è possibile creare un report impaginato o aprire un report dal server di report.  
  
## Per avviare [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] in modalità integrata SharePoint  
  
1.  Accedere al sito di SharePoint che contiene la raccolta desiderata.  
  
2.  Aprire la raccolta.  
  
3.  Fare clic su **Documenti**.  
  
4.  Scegliere **Report di Generatore report** dal menu **Nuovo documento**.  
  
     La prima volta viene avviata la Configurazione guidata di [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] per SQL Server. Per ulteriori informazioni, vedere [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md) .  
  
     [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] ed è possibile creare un report impaginato o aprire un report nel server di report.  
  
     **Nota** Se nel menu **Nuovo documento** non sono elencati **Report di Generatore report**, **Modello di Generatore report**e **Origine dati report**, i relativi tipi di contenuto devono essere aggiunti alla raccolta di SharePoint. Per altre informazioni, vedere [Aggiungere i tipi di contenuto di Reporting Services a una raccolta di SharePoint](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).  
  
## Vedere anche  
 [Generatore report in SQL Server 2016](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [Impostare le opzioni predefinite per Generatore Report](../../reporting-services/report-builder/set-default-options-for-report-builder.md)  
  
  