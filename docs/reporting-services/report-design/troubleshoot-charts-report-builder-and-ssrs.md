---
title: Risolvere i problemi relativi ai grafici (Generatore report e SSRS) | Microsoft Docs
ms.custom: 
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
caps.latest.revision: 
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3d9c4af51de2ac435bbdcefe1d66e0d0a59326e5
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Risoluzione dei problemi relativi ai grafici (Generatore report e SSRS)
  Queste informazioni possono essere utili in caso di utilizzo di grafici.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Nel grafico viene eseguito il conteggio, anziché la somma, dei valori sull'asse dei valori  
 Per tracciare correttamente la maggior parte dei grafici, sono necessari valori numerici lungo l'asse dei valori, che in genere corrisponde all'asse Y. Se il tipo di dati del campo valori è **String**, non sarà possibile visualizzare un valore numerico, neanche se nei campi sono presenti numeri. Viene invece visualizzato un conteggio del numero totale di righe che contengono un valore in tale campo. Per evitare questo comportamento, assicurarsi che i campi utilizzati per le serie di valori abbiano tipi di dati numerici anziché stringhe che contengono numeri formattati.  

## <a name="need-more-help"></a>Per ulteriore assistenza  
   
  Provare:  
 * [SQL Server Reporting Services](https://stackoverflow.com/questions/tagged/reporting-services) su Stack Overflow  
 * Inserire un problema o un suggerimento in [Microsoft SQL Server UserVoice](https://feedback.azure.com/forums/908035-sql-server).  
  
## <a name="see-also"></a>Vedere anche  
 [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
