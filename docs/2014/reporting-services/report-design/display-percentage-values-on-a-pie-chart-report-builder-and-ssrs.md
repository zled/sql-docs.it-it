---
title: Display Percentage Values on a Pie Chart (Report Builder and SSRS) (Visualizzare i valori in percentuale in un grafico a torta (Generatore report e SSRS)) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: eb905fc1-5235-4773-a27e-b07be9318be5
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: d8c4cc67ad7a3719db277840e4ca535a373e8b44
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37287017"
---
# <a name="display-percentage-values-on-a-pie-chart-report-builder-and-ssrs"></a>Visualizzare i valori in percentuale in un grafico a torta (Generatore report e SSRS)
  Per impostazione predefinita, nella legenda vengono visualizzate categorie per identificare ogni valore. Se nel grafico a torta si utilizzano etichette di categorie, è possibile scegliere di mostrare le percentuali nella legenda.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-percentage-values-as-labels-on-a-pie-chart"></a>Per visualizzare valori in percentuale come etichette in un grafico a torta  
  
1.  Aggiungere un grafico a torta al report. Per altre informazioni, vedere [Aggiungere un grafico a un report &#40;Generatore report e SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md).  
  
2.  Nell'area di progettazione fare clic con il pulsante destro del mouse sulla torta e scegliere **Mostra etichette dati**. Le etichette dati dovrebbero apparire in ogni sezione del grafico a torta.  
  
3.  Nell'area di progettazione fare clic con il pulsante destro del mouse sulle etichette e scegliere **Proprietà etichetta serie**. Verrà visualizzata la finestra di dialogo **Proprietà etichetta serie** .  
  
4.  Tipo di `#PERCENT` per il **dati etichetta** opzione.  
  
5.  (Facoltativo) Per specificare il numero di cifre decimali da visualizzare nell'etichetta, digitare "#PERCENT{P*n*}" dove *n* è il numero di cifre decimali da visualizzare. Ad esempio per non visualizzare posizioni decimali, digitare "#PERCENT{P0}."  
  
### <a name="to-display-percentage-values-in-the-legend-of-a-pie-chart"></a>Per visualizzare valori in percentuale nella legenda di un grafico a torta  
  
1.  Nell'area di progettazione fare clic con il pulsante destro del mouse sul grafico a torta e scegliere **Proprietà serie**. Verrà visualizzata la finestra di dialogo **Proprietà serie** .  
  
2.  Nelle **legenda**, digitare `#PERCENT` per il **testo legenda personalizzato** proprietà.  
  
## <a name="see-also"></a>Vedere anche  
 [I grafici a torta &#40;Report e SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Formattazione della legenda in un grafico &#40;Report e SSRS&#41;](chart-legend-formatting-report-builder.md)   
 [Le etichette dei punti di visualizzazione dei dati all'esterno di un grafico a torta &#40;Report e SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [Raccogliere piccole sezioni in un grafico a torta &#40;Report e SSRS&#41;](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)  
  
  
