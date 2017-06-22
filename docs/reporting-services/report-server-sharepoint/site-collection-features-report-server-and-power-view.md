---
title: Attivare il Server di Report Power View Integration Features in SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f64a54-c555-4d31-bf99-3abe57dc8626
caps.latest.revision: 6
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: bca4115307f7bf9dab5ffc9d2ab02ababb209d65
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="site-collection-features---report-server-and-power-view"></a>Caratteristiche raccolta siti, Server di Report e Power View
  Le funzionalità delle raccolte siti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sono in genere attivate per impostazione predefinita dopo l'installazione del componente aggiuntivo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] per prodotti SharePoint. In alcune situazioni sarà necessario attivare manualmente le funzionalità.  
  
 Se si installa il componente aggiuntivo di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per Prodotti SharePoint 2010 dopo l'installazione del prodotto SharePoint, la funzionalità di integrazione del server di report e la funzionalità di integrazione di Power View saranno attivate solo per le raccolte siti radice. Per le altre raccolte siti, sarà necessario attivare manualmente le funzionalità. Ad esempio, se è presente una raccolta siti **http://[nome server]/sites/[nome raccolta siti]** , sarà necessario attivare manualmente le funzionalità delle raccolte siti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Se non è presente alcuna raccolta siti radice, il componente aggiuntivo [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] registra un messaggio simile al seguente.  
  
 "L'applicazione Web SharePoint 80 non dispone della raccolta siti radice"  
  
 Il messaggio sarà registrato nel log dell'installazione del componente aggiuntivo, denominato "RS_SP_#.log" dove # è un numero incrementale. Il file di log si trova nella cartella Temp dell'utente corrente, ad esempio C:\Utenti\\[nome utente]\AppData\Local\Temp. Per altre informazioni sulle opzioni di registrazione con il componente aggiuntivo, vedere [Installare o disinstallare il componente aggiuntivo Reporting Services per SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
 Contenuto dell'argomento:  
  
-   [Per attivare le funzionalità di raccolta siti di integrazione per Power View e server di report](#bkmk_features)  
  
-   [Per attivare o disattivare la funzionalità Raccolta siti di amministrazione centrale di Reporting Services:](#bkmk_centraladmin)  
  
##  <a name="bkmk_features"></a> Per attivare le funzionalità di raccolta siti di integrazione per Power View e server di report  
  
1.  Aprire il browser al sito dove si desidera che le funzionalità [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] siano attive.  
  
2.  Fare clic su **Azioni sito**.  
  
3.  Fare clic su **Impostazioni sito**.  
  
4.  Fare clic su **Funzionalità raccolta siti** nel gruppo Amministrazione raccolta siti  
  
5.  Individuare **Funzionalità di integrazione Server report** o **Funzionalità di integrazione Power View** nell'elenco.  
  
6.  Fare clic su **Attiva**.  
  
 Per disattivare le funzionalità, è possibile utilizzare la stessa procedura facendo clic su **Disattiva** anziché su **Attiva**.  
  
##  <a name="bkmk_centraladmin"></a> Per attivare o disattivare la funzionalità Raccolta siti di amministrazione centrale di Reporting Services:  
  
1.  Aprire il browser alla pagina Amministrazione centrale SharePoint.  
  
2.  Fare clic su **Azioni sito**.  
  
3.  Fare clic su **Impostazioni sito**.  
  
4.  Fare clic su **Funzionalità raccolta siti** nel gruppo Amministrazione raccolta siti  
  
5.  Individuare **Funzionalità Amministrazione centrale del server di report** nell'elenco.  
  
6.  Fare clic su **Attiva**.  
  
 Per disattivare la funzionalità, è possibile utilizzare la stessa procedura facendo tuttavia clic su **Disattiva** anziché su **Attiva.**  
  
## <a name="next-steps"></a>Passaggi successivi  
 Dopo aver attivato la funzionalità, è possibile continuare con l'integrazione del server.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare o disinstallare il componente aggiuntivo Reporting Services per SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  
