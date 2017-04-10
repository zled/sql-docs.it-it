---
title: "Attivare la funzionalit&#224; Sincronizzazione file server di report in Amministrazione centrale SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
caps.latest.revision: 9
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 9
---
# Attivare la funzionalit&#224; Sincronizzazione file server di report in Amministrazione centrale SharePoint
  La funzionalità Sincronizzazione file server di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prevede l'utilizzo di gestori di eventi di SharePoint per sincronizzare il catalogo del server di report con gli elementi nelle raccolte documenti. Questa funzionalità è utile quando gli utenti caricano di frequente elementi di report pubblicati direttamente nelle raccolte documenti di SharePoint. Se la funzionalità di sincronizzazione file non è attivata, il contenuto viene comunque sincronizzato, ma meno frequentemente.  
  
 La funzionalità di sincronizzazione file può essere attivata in Amministrazione sito di SharePoint dopo aver installato il componente aggiuntivo [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] per prodotti SharePoint.  
  
 Tale caratteristica può essere attivata e disattivata manualmente per il sito ma non a livello di raccolta siti.  
  
## Prerequisiti  
 È necessario installare il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per SharePoint. Se il componente aggiuntivo per SharePoint non è installato, la caratteristica di sincronizzazione file non verrà visualizzata nell'elenco delle caratteristiche.  
  
 Per verificare l'installazione, visualizzare l'elenco delle applicazioni installate nel [!INCLUDE[msCoName](../../includes/msconame-md.md)] Pannello di controllo **di**Windows. Se il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è installato, seguire le indicazioni fornite in questo argomento per attivare la caratteristica di sincronizzazione file del server di report.  
  
### Per attivare o disattivare la funzionalità di sincronizzazione file di Reporting Services in un sito  
  
1.  Nella pagina principale del sito scegliere **Impostazioni sito** dal menu **Azioni sito**.  
  
2.  In **Azioni sito** fare clic su **Gestisci caratteristiche sito**.  
  
3.  Trovare **Sincronizzazione file server di report** nell'elenco.  
  
4.  Fare clic su **Attiva**.  
  
> [!NOTE]  
>  Per disattivare la funzionalità di sincronizzazione file del server di report, è possibile seguire la stessa procedura facendo però clic su **Disattiva**.  
  
## Vedere anche  
 [Risoluzione dei problemi relativi alle parti del report (Generatore report e SSRS)](http://msdn.microsoft.com/it-it/d9fe1932-46e7-421b-a8a9-4c54d9576e94)   
 [Attivare le funzionalità di integrazione per Power View e server di report in SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Installare o disinstallare il componente aggiuntivo Reporting Services per SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Installare o disinstallare il componente aggiuntivo Reporting Services per SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  