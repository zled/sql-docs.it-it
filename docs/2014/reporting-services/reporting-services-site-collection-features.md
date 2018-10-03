---
title: Caratteristiche raccolta siti di Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 1bf79e0cfdb6ab21011ec35ba0cf1536f852e04f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48182811"
---
# <a name="reporting-services-site-collection-features"></a>Funzionalità della raccolta siti di Reporting Services
  La modalità SharePoint di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fornisce funzionalità della raccolta siti di SharePoint. Le funzionalità supportano generali [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ambiente di report in modalità SharePoint [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)], una funzionalità delle [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] aggiuntivo per [!INCLUDE[SPS2010](../includes/sps2010-md.md)] Enterprise Edition e le operazioni di gestione per [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in Amministrazione centrale SharePoint.  
  
## <a name="site-collection-features"></a>Funzionalità della raccolta siti  
 Nella tabella seguente vengono descritte le funzionalità della raccolta siti di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Funzionalità|Description|  
|-------------|-----------------|  
|**Funzionalità Amministrazione centrale del server di report**|Consente di abilitare le funzionalità per la gestione dell'integrazione con un server di report [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Questa funzionalità viene installata e utilizzata solo nella raccolta siti di Amministrazione centrale SharePoint.<br /><br /> La funzionalità di integrazione server Report viene attivata automaticamente nella raccolta di siti di amministrazione centrale SharePoint dopo aver installato il [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] aggiuntivo per prodotti SharePoint. In alcune situazioni sarà necessario attivare manualmente la funzionalità. Per attivare la funzionalità del server di report, usare le pagine di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] nella pagina Impostazioni del sito di Amministrazione centrale SharePoint.<br /><br /> Il [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] versione e successive del componente aggiuntivo per SharePoint prodotti attiva la funzionalità di integrazione server report per tutte le raccolte siti esistenti quando viene installato il componente aggiuntivo. La funzionalità risulterà inoltre attivata automaticamente per le nuove raccolte siti.|  
|**Funzionalità di integrazione con il server di report**|Consente di generare report avanzati tramite [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<br /><br /> Questa funzionalità è attiva per impostazione predefinita.|  
|**Funzionalità di integrazione di Power View**|Consente l'esplorazione dei dati interattiva e la presentazione visiva in base a cartelle di lavoro di PowerPivot e database tabulari di Analysis Services.<br /><br /> L'accesso alla funzionalità può essere eseguito dai menu di scelta rapida delle origini dati seguenti:<br /><br /> rdlx<br /><br /> rsds<br /><br /> file di connessione bism<br /><br /> <br /><br /> Se [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] non è visualizzato nei menu di scelta rapida, verificare che la **Funzionalità di integrazione Power View** sia attivata.<br /><br /> Questa funzionalità è disattivata per impostazione predefinita.|  
  
## <a name="see-also"></a>Vedere anche  
 [Attivare le funzionalità di integrazione Power View in SharePoint e il Server di Report](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)   
 [Report funzionalità e impostazioni del sito servizi&#40;modalità SharePoint&#41;](../../2014/reporting-services/reporting-services-site-settings-and-site-features-sharepoint-mode.md)   
 [Attivare la funzionalità Sincronizzazione file server di report in Amministrazione centrale SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md)  
  
  
