---
title: "Funzionalità di Reporting Services sito raccolta | Documenti Microsoft"
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: 7c86f9ecdbbf4955ba224e40c245fc412742fc30
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="reporting-services-site-collection-features"></a>Funzionalità di Reporting Services sito raccolta

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

Reporting Services in modalità SharePoint fornisce tre caratteristiche raccolta siti di SharePoint. Le funzionalità supportano la modalità SharePoint di Reporting Services generale, ambiente di report [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], una funzionalità di SQL Server 2016 Reporting Services aggiuntivo le operazioni di gestione per Reporting Services in Amministrazione centrale SharePoint.

> [!NOTE]
> Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.
  
## <a name="site-collection-features"></a>Caratteristiche raccolta siti

 Nella tabella seguente descrive le funzionalità di raccolta del sito di Reporting Services.  
  
|Funzionalità|Description|  
|-------------|-----------------|  
|**Funzionalità Amministrazione centrale del server di report**|Abilita le funzionalità per gestire l'integrazione con un server di report di Reporting Services. Questa funzionalità viene installata e utilizzata solo nella raccolta siti di Amministrazione centrale SharePoint.<br /><br /> La funzionalità di integrazione del server di report viene attivata automaticamente nella raccolta siti di Amministrazione centrale SharePoint dopo aver installato il componente aggiuntivo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] per prodotti SharePoint. In alcuni casi, è necessario attivare manualmente la funzionalità. Per attivare la funzionalità server di report, utilizzare le pagine di Reporting Services nella pagina Impostazioni sito di amministrazione centrale SharePoint.<br /><br /> Il [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] versione di Reporting Services e versioni successive del componente aggiuntivo per SharePoint prodotti attivare la funzionalità di integrazione server report per tutte le raccolte siti esistenti quando viene installato il componente aggiuntivo. Inoltre, la funzionalità è attivata automaticamente per le nuove raccolte siti.|  
|**Funzionalità di integrazione con il server di report**|Consente di generare report avanzati tramite [!INCLUDE[msCoName](../../includes/msconame-md.md)] Reporting Services<br /><br /> Questa funzionalità è attiva per impostazione predefinita.|  
|**Funzionalità di integrazione di Power View**|Consente l'esplorazione dei dati interattiva e la presentazione visiva su cartelle di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e database tabulari di Analysis Services.<br /><br /> L'accesso alla funzionalità può essere eseguito dai menu di scelta rapida delle origini dati seguenti:<br /><br /> **rdlx**<br /><br /> **rsds**<br /><br /> File di connessione con estensione**bism** <br /><br /> <br /><br /> Se [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] non è visualizzato nei menu di scelta rapida, verificare che la **Funzionalità di integrazione Power View** sia attivata.<br /><br /> Questa funzionalità è disattivata per impostazione predefinita.|  

## <a name="next-steps"></a>Passaggi successivi

[Attivare le funzionalità di integrazione per Power View e server di report in SharePoint](../../reporting-services/report-server-sharepoint/site-collection-features-report-server-and-power-view.md)   
[Funzionalità e impostazioni del sito di Reporting Services &#40;modalità SharePoint&#41;](../../reporting-services/report-server-sharepoint/site-settings-and-features-reporting-services.md)   
[Attivare la funzionalità Sincronizzazione file server di report in Amministrazione centrale SharePoint](../../reporting-services/report-server-sharepoint/activate-the-report-server-file-sync-feature-in-sharepoint-ca.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

