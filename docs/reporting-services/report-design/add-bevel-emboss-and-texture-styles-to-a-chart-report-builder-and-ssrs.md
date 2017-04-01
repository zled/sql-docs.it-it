---
title: "Aggiungere stili smussato, rilievo e trama a un grafico (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 737cfc80-b39e-497c-817b-b46693deb58f
caps.latest.revision: 6
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Aggiungere stili smussato, rilievo e trama a un grafico (Generatore report e SSRS)
  Quando si utilizzano determinati tipi di grafico, è possibile specificare un effetto di disegno per aumentarne l'effetto visivo. Tali effetti vengono applicati solo alle serie, mentre non influiscono su altri elementi del grafico.  
  
 Quando si utilizza una variante di un grafico a torta o ad anello, è possibile specificare uno stile di disegno con contorni sfumati o concavo, simile agli effetti smussato o rilievo applicabili a un'immagine.  
  
 Quando si utilizza una variante di un grafico a barre o di un istogramma, è possibile applicare stili di trama, ad esempio cilindro, spicchio e chiaroscuro, alle singole barre o colonne.  
  
 Oltre a questi stili di disegno, è possibile aggiungere bordi e ombreggiature a molti elementi del grafico per conferire un effetto ottico di profondità. Per altre informazioni su altri modi per formattare il grafico, vedere [Formattazione di un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Per aggiungere gli stili smussato o rilievo a un grafico a torta o ad anello  
  
1.  Nella scheda **Visualizza** selezionare **Proprietà** per aprire il riquadro Proprietà.  
  
2.  Selezionare il grafico a torta o ad anello che si desidera ottimizzare. Selezionare un campo di dati nel grafico, non tutto il grafico.  
  
3.  Nel riquadro Proprietà espandere il nodo **CustomAttributes** .  
  
4.  Per PieDrawingStyle selezionare uno stile dall'elenco a discesa.  
  
> [!NOTE]  
>  Non è possibile disporre di stili 3D e smussato o rilievo nello stesso grafico. Una volta abilitato lo stile 3D per il grafico, la proprietà PieDrawingStyle non verrà visualizzata.  
  
 ![Grafico a torta con stile di disegno concavo](../../reporting-services/report-design/media/rs-piedrawingeffects-concave.png "Grafico a torta con stile di disegno concavo")  
  
### Per aggiungere gli stili di trama a un grafico a barre o a un istogramma  
  
1.  Selezionare il grafico a barre o l'istogramma che si desidera ottimizzare. Selezionare un campo di dati nel grafico, non tutto il grafico.  
  
2.  Aprire il riquadro Proprietà.  
  
3.  Espandere il nodo **CustomAttributes** .  
  
4.  Per DrawingStyle selezionare uno stile dall'elenco a discesa.  
  
> [!NOTE]  
>  Non è possibile disporre di stili 3D e smussato o rilievo nello stesso grafico. Una volta abilitato lo stile 3D per il grafico, la proprietà PieDrawingStyle non verrà visualizzata.  
  
 ![Grafico a barre con effetto di disegno LightToDark](../../reporting-services/report-design/media/rs-bardrawingeffects-lighttodark.gif "Grafico a barre con effetto di disegno LightToDark")  
  
## Vedere anche  
 [Grafici a barre &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/bar-charts-report-builder-and-ssrs.md)   
 [Istogrammi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/column-charts-report-builder-and-ssrs.md)   
 [Grafici a torta &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)   
 [Formattazione di un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)  
  
  