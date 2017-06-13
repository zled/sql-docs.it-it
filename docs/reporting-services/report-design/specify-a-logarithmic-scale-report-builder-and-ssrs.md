---
title: Specificare una scala logaritmica (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3092c1c-b128-433d-9a95-983508b2a8d4
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3cbd1de3393757c20cf31c76be12d2911ecf7f9f
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="specify-a-logarithmic-scale-report-builder-and-ssrs"></a>Specificare una scala logaritmica (Generatore report e SSRS)
  Se i dati sono proporzionali in modo logaritmico, è opportuno usare una scala logaritmica in un grafico di un report impaginato di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] . per migliorare l'aspetto del grafico e agevolare la gestione dei dati. Con la maggior parte delle scale logaritmiche viene utilizzata la base 10.  
  
 Questa caratteristica è disponibile solo sull'asse dei valori. L'asse dei valori è in genere l'asse verticale, ovvero l'asse Y. Sui grafici a barre, tuttavia, è l'asse orizzontale, ovvero l'asse x.  
  
 Se l'asse è logaritmico, tutte le altre proprietà correlate all'asse verranno scalate in modo logaritmico. Se ad esempio si specifica una scala logaritmica in base 10 sull'asse e si imposta per l'asse un intervallo di 2, verranno generati intervalli con ordine di grandezza pari a 10 alla potenza di 2 o 100. Ciò significa che i valori dell'asse indicheranno 1, 100, 10000, anziché il risultato predefinito 1, 10, 100, 1000, 10000.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-specify-a-logarithmic-scale"></a>Per specificare una scala logaritmica  
  
1.  Fare clic con il pulsante destro del mouse sull'asse Y del grafico e scegliere **Proprietà asse verticale**. Viene visualizzata la finestra di dialogo **Proprietà asse verticale** .  
  
2.  In **Opzioni asse**selezionare **Usa scala logaritmica**.  
  
3.  Nella casella di testo **Base logaritmo** digitare un valore positivo per la base logaritmica. Se non si specifica alcun valore, il valore predefinito della base logaritmica sarà 10.  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione delle etichette degli assi in un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Formattazione di un grafico &#40Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Formattazione delle etichette degli assi come date o valute &#40;Generatore report e SSRSSSRS&#41;](../../reporting-services/report-design/format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
