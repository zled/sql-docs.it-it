---
title: "Prerequisiti per le esercitazioni (Generatore report) | Microsoft Docs"
ms.custom: ""
ms.date: "06/15/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: 11
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Prerequisiti per le esercitazioni (Generatore report)
Per eseguire le esercitazioni di Generatore report è necessario essere in grado di visualizzare e salvare i report impaginati di [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] in un server di report o in un sito di SharePoint integrato in un server di report. Per quanto riguarda i dati, in tutte le esercitazioni vengono utilizzate query letterali che devono essere elaborate da un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
Se non si dispone dell'accesso a un server di report, a un sito o a un'origine dati, sarà possibile apprendere l'utilizzo di Generatore report attraverso la compilazione di un report offline. Vedere [Esercitazione: Creare un report grafico rapido offline &#40;Generatore report&#41;](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  
  
## Requisiti  
Per completare le esercitazioni di Generatore report, è necessario soddisfare i requisiti seguenti:  
  
-   Accesso a Generatore report di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. È possibile eseguire Generatore report da un server di report di [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] o un server di report di [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] in modalità integrata SharePoint. Nei diversi tipi di server l'unica differenza riguarda il primo passaggio, ovvero l'apertura di Generatore report.  
  
    In un server di report selezionare **Nuovo** > **Report impaginato**.
  
    In un server di report in modalità integrata SharePoint, nella scheda **Documenti** selezionare **Nuovo documento**, quindi selezionare **Report di Generatore report** nell'elenco a discesa. Ad esempio, `http://<servername>/sites/mySite/reports`. L'amministratore di SharePoint deve abilitare la caratteristica Report di Generatore report per ogni raccolta documenti.  
  
-   URL di un server di report di [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] o di un sito di SharePoint integrato con un server di report di [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)]. È necessario disporre dell'autorizzazione per il salvataggio e la visualizzazione di report, origini dati condivise, set di dati condivisi, parti di report e modelli. Per impostazione predefinita, l'URL per un server di report è `http://<servername>/reportserver`. Per impostazione predefinita, l'URL per un sito SharePoint è `http://<sitename>` o `http://<server>/site`.  
  
-   Nome di un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] e credenziali sufficienti per l'accesso in sola lettura a qualsiasi database. Per le query del set di dati delle esercitazioni vengono utilizzati dati letterali, ma per restituire i metadati necessari per un set di dati del report ogni query deve essere elaborata da un'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]. Ad esempio, nella stringa di connessione seguente viene specificato solo un server: `data source=<servername>`. È necessario disporre dell'accesso in lettura al database predefinito assegnato all'utente dall'amministratore di sistema che concede l'autorizzazione per l'accesso al server. È inoltre possibile specificare un database, come illustrato nella stringa di connessione seguente: `data source=<servername>;initial catalog=<database>`.  
  
-   Per [l'esercitazione relativa al report mappa](Tutorial:%20Map%20Report%20\(Report%20Builder\).md) è necessario configurare il server di report affinché supporti le mappe Bing come sfondo. Per altre informazioni, vedere [Pianificare il supporto dei report mappa](http://msdn.microsoft.com/it-it/5ddc97a7-7ee5-475d-bc49-3b814dce7e19).   

-   L'esercitazione [Creazione di report drill-through e report principali](Tutorial:%20Creating%20Drillthrough%20and%20Main%20Reports%20\(Report%20Builder\).md) richiede l'accesso al cubo Contoso Sales. Per altre informazioni, vedere l'esercitazione. 
  
L'amministratore del server di report deve concedere le autorizzazioni necessarie per il server di report, configurare i percorsi delle cartelle [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] e configurare le opzioni predefinite di Generatore report. Per altre informazioni, vedere [Installare e disinstallare Generatore report](../Topic/Install%20and%20Uninstall%20Report%20Builder.md).  
  
## Vedere anche  
[Esercitazioni di Generatore report](../reporting-services/report-builder-tutorials.md)  
  
