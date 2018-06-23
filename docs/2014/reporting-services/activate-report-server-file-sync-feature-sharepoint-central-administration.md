---
title: Attivare la funzionalità sincronizzazione File Server di Report in Amministrazione centrale SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 32d1988d-07e7-41c2-b636-e65ecfae4677
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 83ffe3e16bad4fdc1c60a818dd7f07bd47e00cb8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169840"
---
# <a name="activate-the-report-server-file-sync-feature-in-sharepoint-central-administration"></a>Attivare la funzionalità Sincronizzazione file server di report in Amministrazione centrale SharePoint
  La funzionalità Sincronizzazione file server di report di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] prevede l'utilizzo di gestori di eventi di SharePoint per sincronizzare il catalogo del server di report con gli elementi nelle raccolte documenti. Questa funzionalità è utile quando gli utenti caricano di frequente elementi di report pubblicati direttamente nelle raccolte documenti di SharePoint. Se la funzionalità di sincronizzazione file non è attivata, il contenuto viene comunque sincronizzato, ma meno frequentemente.  
  
 La caratteristica sincronizzazione File può essere attivata in Amministrazione sito di SharePoint dopo aver installato il [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] aggiuntivo per prodotti SharePoint.  
  
 Tale caratteristica può essere attivata e disattivata manualmente per il sito ma non a livello di raccolta siti.  
  
## <a name="prerequisites"></a>Prerequisiti  
 È necessario installare il componente aggiuntivo [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per SharePoint. Se il componente aggiuntivo per SharePoint non è installato, la caratteristica di sincronizzazione file non verrà visualizzata nell'elenco delle caratteristiche.  
  
 Per verificare l'installazione, visualizzare l'elenco delle applicazioni installate nel [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows **Pannello di controllo**. Se il [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] aggiuntivo viene installato, seguire le istruzioni in questo argomento per attivare la funzionalità di sincronizzazione file server di report.  
  
### <a name="to-activate-or-deactivate-the-reporting-services-file-sync-feature-on-a-site"></a>Per attivare o disattivare la funzionalità di sincronizzazione file di Reporting Services in un sito  
  
1.  Nella pagina principale del sito scegliere **Impostazioni sito** dal menu **Azioni sito**.  
  
2.  In **Azioni sito** fare clic su **Gestisci caratteristiche sito**.  
  
3.  Trovare **Sincronizzazione file server di report** nell'elenco.  
  
4.  Fare clic su **Attiva**.  
  
> [!NOTE]  
>  Per disattivare la funzionalità di sincronizzazione file del server di report, è possibile seguire la stessa procedura facendo però clic su **Disattiva**.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi relativi a parti del Report &#40;SSRS e Generatore Report&#41;](report-parts-report-builder-and-ssrs.md)   
 [Attivare il Server di Report Power View Integration Features in SharePoint](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Installare o disinstallare il componente aggiuntivo di servizi Reporting per SharePoint &#40;SharePoint 2010 e SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)   
 [Installare o disinstallare il componente aggiuntivo di servizi Reporting per SharePoint &#40;SharePoint 2010 e SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  