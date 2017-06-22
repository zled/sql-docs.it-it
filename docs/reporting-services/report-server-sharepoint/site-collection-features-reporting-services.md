---
title: Caratteristiche raccolta siti di Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e05ae162-a4b2-489d-9853-d6b09414e632
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b68204ab4c9a008db7c43d2c568d1c3ccedbcb7a
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---

# <a name="site-collection-features---reporting-services"></a>Caratteristiche raccolta siti - Reporting Services

[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] La modalità SharePoint fornisce tre funzionalità della raccolta siti di SharePoint. Le funzionalità supportano generale [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ambiente di report in modalità SharePoint [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], una funzionalità di SQL Server 2016 Reporting Services aggiuntivo le operazioni di gestione per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in Amministrazione centrale SharePoint.  
  
## <a name="site-collection-features"></a>Funzionalità della raccolta siti  
 Nella tabella seguente vengono descritte le funzionalità della raccolta siti di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
|Funzionalità|Description|  
|-------------|-----------------|  
|**Funzionalità Amministrazione centrale del server di report**|Consente di abilitare le funzionalità per la gestione dell'integrazione con un server di report [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Questa funzionalità viene installata e utilizzata solo nella raccolta siti di Amministrazione centrale SharePoint.<br /><br /> La funzionalità di integrazione del server di report viene attivata automaticamente nella raccolta siti di Amministrazione centrale SharePoint dopo aver installato il componente aggiuntivo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] per prodotti SharePoint. In alcune situazioni sarà necessario attivare manualmente la funzionalità. Per attivare la funzionalità del server di report, usare le pagine di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nella pagina Impostazioni del sito di Amministrazione centrale SharePoint.<br /><br /> [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e versioni successive del componente aggiuntivo per prodotti SharePoint attiva la funzionalità di integrazione del server di report per tutte le raccolte siti esistenti al momento dell'installazione del componente aggiuntivo. La funzionalità risulterà inoltre attivata automaticamente per le nuove raccolte siti.|  
|**Funzionalità di integrazione con il server di report**|Consente la creazione di report avanzata tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<br /><br /> Questa funzionalità è attiva per impostazione predefinita.|  
|**Funzionalità di integrazione di Power View**|Consente l'esplorazione dei dati interattiva e la presentazione visiva su cartelle di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e database tabulari di Analysis Services.<br /><br /> L'accesso alla funzionalità può essere eseguito dai menu di scelta rapida delle origini dati seguenti:<br /><br /> **rdlx**<br /><br /> **rsds**<br /><br /> File di connessione con estensione**bism** <br /><br /> <br /><br /> Se [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] non è visualizzato nei menu di scelta rapida, verificare che la **Funzionalità di integrazione Power View** sia attivata.<br /><br /> Questa funzionalità è disattivata per impostazione predefinita.|  

## <a name="next-steps"></a>Passaggi successivi

[Attivare le funzionalità di integrazione per Power View e server di report in SharePoint](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)   
[Le impostazioni del sito e le funzionalità del sito &#40; di Reporting Services Modalità SharePoint &#41;](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)   
[Attivare la funzionalità Sincronizzazione file server di report in Amministrazione centrale SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
