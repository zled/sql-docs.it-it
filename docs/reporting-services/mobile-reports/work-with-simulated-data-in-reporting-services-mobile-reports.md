---
title: Lavorare con dati simulati nei report di Reporting Services per dispositivi mobili | Microsoft Docs
ms.custom: SQL2016_New_Updated
ms.date: 02/08/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6baabc36-58fb-4a98-bb9c-c42bafb16d0f
caps.latest.revision: "9"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 84d3282dc887d43798e1bfdb0c0e18554b85d1a1
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="work-with-simulated-data-in-reporting-services-mobile-reports"></a>Lavorare con dati simulati nei report di Reporting Services per dispositivi mobili
Quando si inserisce un elemento della raccolta nell'area di progettazione, [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] genera immediatamente dati simulati per quell'elemento. Questi dati assolvono a molti scopi utili durante la creazione di report per dispositivi mobili.   
  
![SS_MRP_SimDataTreeMapProps](../../reporting-services/mobile-reports/media/ss-mrp-simdatatreemapprops.png)  
  
I dati simulati risultano utili quando si adotta un approccio di tipo progettuale alla creazione di report per dispositivi mobili. Il popolamento iniziale degli elementi con dati simulati consente di creare prototipi di report per dispositivi mobili in modo rapido, senza doversi preoccupare di specifici requisiti dei dati. Questi report per dispositivi mobili possono quindi essere valutati in termini generali di estetica ed efficienza.  
  
## <a name="create-an-excel-file-with-simulated-data-as-a-template"></a>Creare un file di Excel con dati simulati come modello  
  
I dati simulati forniscono anche un modello che rappresenta in modo accurato i requisiti dei dati di un determinato progetto di report per dispositivi mobili.   
  
-  Click **Esporta tutti i dati** nell'angolo in alto a destra della Vista dati.   
  
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] genera un documento di Excel contenente dati simulati, che possono essere sostituiti rapidamente con dati reali, pronto per l'importazione.   
  
## <a name="how-simulated-data-behaves"></a>Comportamento dei dati simulati  
  
I dati simulati generati sono personalizzati in modo specifico per il report per dispositivi mobili che si sta creando. Man mano che si posizionano altri elementi nell'area di progettazione, i dati simulati associati aumentano e cambiano per fornire la migliore esperienza possibile in assenza di dati reali. Questa evoluzione assicura la possibilità di disporre di altri campi e filtri nel caso in cui si aggiungano serie supplementari nelle visualizzazioni grafico o si espanda altrimenti l'ambito di uno o più elementi dei report per dispositivi mobili.  
  
Come accennato in precedenza, è possibile esportare dati simulati in un file di Excel, creando un modello di dati ideale per il report per dispositivi mobili associato. È possibile scambiare i dati con i dati reali nel file di Excel e reimportarli in [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)].   
  
Dopo avere associato tutti i controlli a dati reali, le tabelle simulate non più in uso vengono rimosse automaticamente dal report per dispositivi mobili. Non è possibile rimuovere tabelle simulate a cui fanno ancora riferimento elementi nell'area di progettazione.  
  
>**Nota**: i dati simulati non contribuiscono al footprint complessivo del report per dispositivi mobili perché non sono serializzati con tale report, ma vengono generati in fase di esecuzione.  
  
### <a name="see-also"></a>Vedere anche  
- [Creare e pubblicare report per dispositivi mobili con SQL Server Mobile Report Publisher](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  Vedere [Visualizzare report per dispositivi mobili e indicatori KPI di SQL Server nell'app iPad](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  (Power BI per iOS)  
-  [Visualizzare report per dispositivi mobili e indicatori KPI di SQL Server nell'app iPhone](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports) (Power BI per iOS)  
  
  
  
  
  

