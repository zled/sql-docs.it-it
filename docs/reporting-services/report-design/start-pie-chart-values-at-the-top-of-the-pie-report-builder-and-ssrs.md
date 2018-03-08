---
title: Start Pie Chart Values at the Top of the Pie (Report Builder and SSRS) (Iniziare a visualizzare i valori del grafico a torta dalla parte superiore (Generatore report e SSRS)) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0e6fb59-ca4e-4d70-97cb-0ad183da21d3
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e77b16fa5f4466201d9e3e7a6eaa8b854eb1850d
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="start-pie-chart-values-at-the-top-of-the-pie-report-builder-and-ssrs"></a>Inizio della visualizzazione dei valori del grafico a torta dalla parte superiore (Generatore report e SSRS)
Per impostazione predefinita, nei grafici a torta dei report impaginati di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] il primo valore nel set di dati inizia a 90 gradi dalla cima della torta. 

![report-builder-pie-chart-start-at-90](../../reporting-services/media/report-builder-pie-chart-start-at-90.png)

*I valori del grafico iniziano a 90 gradi.*

È possibile far iniziare il primo valore dalla cima della torta. 

![report-builder-pie-chart-start-at-top](../../reporting-services/media/report-builder-pie-chart-start-at-top.png)

*I valori del grafico iniziano dalla cima della torta.*
  
## <a name="to-start-the-pie-chart-at-the-top-of-the-pie"></a>Per fare iniziare il grafico a torta dalla cima della torta  
  
1.  Fare clic sulla torta stessa.  
  
2.  Se il riquadro **Proprietà** non è visualizzato, fare clic su **Proprietà** nella scheda **Visualizza**  
  
3.  Nel riquadro **Proprietà** , sotto **Attributi personalizzati**modificare **PieStartAngle** da **0** a **270**.  
  
4.  Fare clic su **Esegui** per visualizzare l'anteprima del report.  
  
 Il primo valore inizia ora all'inizio del grafico a torta.  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione di un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Grafici a torta &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  
