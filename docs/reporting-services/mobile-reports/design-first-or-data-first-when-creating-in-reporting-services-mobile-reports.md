---
title: Progettare innanzitutto o con i dati durante la creazione di report per dispositivi mobili di Reporting Services | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 02/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7b355fa-312b-4074-bc9b-776269d4fb51
caps.latest.revision: 17
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8cf203f17ac149825e0e4d79ed7f6f6041700ae4
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="design-first-or-data-first-when-creating-in-reporting-services-mobile-reports"></a>Iniziare con la progettazione o con i dati durante la creazione di report per dispositivi mobili di Reporting Services
  
Con [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)], è possibile creare rapidamente report per dispositivi mobili che si adattano a tutte le dimensioni dello schermo, in un'area di progettazione con righe e colonne della griglia regolabili ed elementi flessibili del report per dispositivi mobili.   
  
Durante la creazione di report per dispositivi mobili è possibile scegliere di due approcci di base: iniziare prima con i dati oppure iniziare prima con la progettazione. [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] supporta entrambi.   
  
## <a name="design-first"></a>Prima la progettazione  
  
Il diagramma seguente illustra i componenti della visualizzazione layout [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] :   
  
![SS_MRP_LayoutTab](../../reporting-services/mobile-reports/media/ss-mrp-layouttab.png)  
  
Nell'approccio diretto prima alla progettazione, è possibile creare un layout del report per dispositivi mobili senza importare alcun dato. È un buon metodo per creare un report per dispositivi mobili quando non si è certi che i dati siano formattati correttamente. Senza dati reali, gli elementi della raccolta vengono associati automaticamente ai dati simulati generati, che è possibile esportare e usare come modello per descrivere i dati richiesti.  
  
## <a name="data-first"></a>Prima i dati  
L'approccio diretto prima ai dati consiste nell'importare in primo luogo tutti i dati richiesti, quindi progettare il report per dispositivi mobili e impostare le proprietà dei dati negli elementi del report. Ciò offre il vantaggio di poter connettere ogni elemento ai dati reali quando si aggiungono al layout. Quando si usa un approccio diretto prima ai dati, assicurarsi che i dati reali siano formattati correttamente per l'uso con [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)].   
  
 Il diagramma seguente illustra tutti i componenti della visualizzazione dati [!INCLUDE[SS_MobileReptPub_Long](../../includes/ss-mobilereptpub-short.md)] :  
  
![SS_MRP_DataTab](../../reporting-services/mobile-reports/media/ss-mrp-datatab.png)  
  
### <a name="see-also"></a>Vedere anche  
- [Creare e pubblicare report per dispositivi mobili con SQL Server Mobile Report Publisher](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  Vedere [Visualizzare report per dispositivi mobili e indicatori KPI di SQL Server nell'app iPad](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI per iOS)  
-  [Visualizzare report per dispositivi mobili e indicatori KPI di SQL Server nell'app iPhone](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI per iOS)  
  
  
  
  


