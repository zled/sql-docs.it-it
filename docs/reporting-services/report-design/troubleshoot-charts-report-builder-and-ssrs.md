---
title: Risolvere i problemi relativi ai grafici (Generatore report e SSRS) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
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
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 76e6a49e935ea5744686be628f6a7138d6feed91
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Risoluzione dei problemi relativi ai grafici (Generatore report e SSRS)
  Queste informazioni possono essere utili in caso di utilizzo di grafici.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Nel grafico viene eseguito il conteggio, anziché la somma, dei valori sull'asse dei valori  
 Per tracciare correttamente la maggior parte dei grafici, sono necessari valori numerici lungo l'asse dei valori, che in genere corrisponde all'asse Y. Se il tipo di dati del campo valori è **String**, non sarà possibile visualizzare un valore numerico, neanche se nei campi sono presenti numeri. Viene invece visualizzato un conteggio del numero totale di righe che contengono un valore in tale campo. Per evitare questo comportamento, assicurarsi che i campi utilizzati per le serie di valori abbiano tipi di dati numerici anziché stringhe che contengono numeri formattati.  
  
## <a name="see-also"></a>Vedere anche  
 [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
