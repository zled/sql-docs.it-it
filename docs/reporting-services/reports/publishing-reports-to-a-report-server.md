---
title: "Pubblicazione dei report in un server di report | Microsoft Docs"
ms.custom: ""
ms.date: "06/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ambienti di produzione [Reporting Services]"
  - "progetti di report [Reporting Services]"
  - "Debug - configurazione [Reporting Services]"
  - "pubblicazione di report [Reporting Services]"
  - "pubblicazione di report [Reporting Services]"
  - "proprietà del report [Reporting Services]"
  - "Progettazione report [Reporting Services], distribuzione di report"
  - "Production - configurazione [Reporting Services]"
  - "pubblicazione di report [Reporting Services], ambienti di produzione"
  - "DebugLocal - configurazione [Reporting Services]"
  - "distribuzione [Reporting Services]. report"
  - "Progettazione report [Reporting Services], pubblicazione di report"
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
caps.latest.revision: 47
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 47
---
# Pubblicazione dei report in un server di report
  Dopo aver progettato e testato un report o un set di report, è possibile usare le caratteristiche della distribuzione disponibili in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per pubblicare i report in un server di report. È possibile pubblicare report singoli o un progetto Server di Report che può includere più report e origini dati. La pubblicazione di un progetto server report è il modo più semplice per pubblicare più report. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] viene usato il termine *distribuire* anziché *pubblicare*. I due termini sono perfettamente equivalenti.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] vengono fornite configurazioni del progetto per gestire la pubblicazione dei report. La configurazione specifica il percorso del server di report, la versione di SQL Server Reporting Services installata nel server di report, l'eventuale sovrascrittura delle origini dati pubblicate nel server di report e così via. Ad esempio, la configurazione "Debug" può pubblicare in un server diverso rispetto alla configurazione di "release". Oltre a usare le configurazioni fornite in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], è possibile crearne di nuove.  
 
## Requisiti per la pubblicazione
L'autorizzazione è determinata dalla sicurezza basata sui ruoli definita dall'amministratore del server di report. In genere le operazioni di pubblicazione vengono concesse tramite il **ruolo Server di pubblicazione**.  
  
## Configurazioni di progetto  
 Nell'ambiente di gestione dei report potrebbero essere installati più server di report e varie versioni di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. È possibile creare più configurazioni e utilizzarne quindi una diversa in base allo scenario di distribuzione. Le configurazioni di progetto includono le proprietà per la compilazione dei report, ad esempio la cartella nella quale archiviare temporaneamente i report compilati e le modalità di gestione dei problemi di compilazione. Le configurazioni dispongono inoltre delle proprietà necessarie per specificare il percorso e la versione del server di report, nonché le cartelle sul server di report.  
  
 Per impostazione predefinita, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] sono disponibili tre configurazioni di progetto: **DebugLocal**, **Debug** e **Release**. La configurazione predefinita è DebugLocal. La configurazione DebugLocal viene usata in genere per visualizzare i report in una finestra di anteprima locale, la configurazione Debug per pubblicare i report in un server di prova e la configurazione Release per pubblicare i report in un server di produzione. Nell'elenco a discesa delle configurazioni della soluzione sulla barra degli strumenti Standard viene indicata la configurazione attiva. Per utilizzare una configurazione diversa, selezionarla dall'elenco.  
  
 ![ssrs_project_properties](../../reporting-services/reports/media/ssrs-project-properties.png) 
  
 Per altre informazioni, vedere quanto segue
 + [Finestra di dialogo Pagine delle proprietà del progetto](../../reporting-services/tools/project-property-pages-dialog-box.md)
 + [Deployment and Version Support in SQL Server Data Tools](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)
 + [Impostare le proprietà di distribuzione per i progetti Reporting Services in SSDT](../../reporting-services/tools/set-deployment-properties-reporting-services.md)
  
## Per pubblicare tutti i report di un progetto  
  
Nel menu **Compila** fare clic su **Distribuisci \<nome progetto report>**. In alternativa, in Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto report e scegliere **Distribuisci**. È possibile visualizzare lo stato del processo di pubblicazione nella finestra Output.  
  
Quando si distribuisce un progetto server di report, vengono distribuite anche le origini dati condivise nel progetto report. Tutti i report vengono distribuiti utilizzando la stessa configurazione di progetto: lo stesso server di report, la stessa cartella sul server e così via. Affinché i report siano destinati a server diversi, è necessario pubblicarli uno alla volta oppure includere nel progetto server di report solo quelli desiderati. In una soluzione possono essere inclusi più progetti server di report. Quando si utilizzano più progetti, la gestione della distribuzione dei report può risultare più semplice, dal momento che è possibile distribuire progetti diversi tramite una diversa configurazione. 
  
## Per pubblicare un solo report  
  
In Esplora soluzioni fare clic con il pulsante destro del mouse sul report e scegliere **Distribuisci**. È possibile visualizzare lo stato del processo di pubblicazione nella finestra Output.  
  
 Quando si pubblica un report, è necessario distribuire anche le origini dati condivise utilizzate dal report.   
 Se non si desidera pubblicare tutti i report di un progetto, si può scegliere di pubblicarne anche uno soltanto. A tale scopo selezionare una configurazione che preveda la distribuzione del report, ad esempio la configurazione Release, fare clic con il pulsante destro del mouse sul report, quindi scegliere **Distribuisci**.  
  
 Se in un report viene utilizzata un'origine dati condivisa, è necessario distribuire anche tale origine. In caso contrario, il report distribuito non verrà eseguito. Fare clic con il pulsante destro del mouse sull'origine dati condivisa, quindi scegliere **Distribuisci**.  
  
 È necessario specificare l'URL del server di destinazione del server di report ed eventualmente modificare le cartelle predefinite nelle quali distribuire i report e le origini dati condivise.  

  
## Vedere anche  
 [Finestra di dialogo Pagine delle proprietà del progetto](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [Gestione contenuto del server di report &#40;modalità nativa SSRS&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Aggiornare i report](../../reporting-services/install-windows/upgrade-reports.md)  
  
  