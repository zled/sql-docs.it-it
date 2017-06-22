---
title: Aggiungere una media mobile a un grafico (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
caps.latest.revision: 13
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f838e4a7e9518587e91dddec6c2cab61c1061232
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="add-a-moving-average-to-a-chart-report-builder-and-ssrs"></a>Aggiungere una media mobile a un grafico (Generatore report e SSRS)
Una media mobile è una media dei dati della serie, calcolata in un periodo di tempo definito. Nei report impaginati [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è possibile indicare la media mobile sul grafico per identificare tendenze significative.  

![report-builder-column-chart-tutorial](../../reporting-services/media/report-builder-column-chart-tutorial.png)
  
 La formula della media mobile è l'indicatore di prezzo più diffuso utilizzato nelle analisi tecniche. Da una serie del grafico è anche possibile derivare molte altre formule, ad esempio media, mediana e deviazione standard. Quando si specifica una media mobile, ogni formula può includere uno o più parametri che devono essere specificati.  
 
 Il [esercitazione: aggiungere un istogramma al Report (Generatore Report)](Tutorial:%20Add%20a%20Column%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md) viene illustrata l'aggiunta di una media mobile al grafico, se si desidera provare con dati di esempio.
  
 Quando si aggiunge una media mobile in modalità progettazione, la serie di linee aggiunta è solo un segnaposto visivo. I punti dati di ogni formula verranno calcolati durante l'elaborazione del report.  
  
 In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]non è disponibile il supporto incorporato per le linee di tendenza.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-calculated-moving-average-to-a-series-on-the-chart"></a>Per aggiungere una media mobile calcolata in una serie del grafico  
  
1.  Fare clic con il pulsante destro del mouse in un campo dell'area **Valori** e scegliere **Aggiungi serie calcolata**. Verrà visualizzata la finestra di dialogo **Proprietà serie calcolata** .  
  
2.  Selezionare l'opzione **Media mobile** dall'elenco a discesa **Formula** .  
  
3.  Specificare un valore intero per **Periodo** , che rappresenta il periodo della media mobile.  
  
    > [!NOTE]  
    >  Il periodo è il numero di giorni utilizzato per calcolare una media mobile. Se sull'asse X non sono rappresentati valori di data/ora, il periodo è rappresentato dal numero di punti dati utilizzati per calcolare una media mobile. Se è disponibile un unico punto dati, la formula della media mobile non viene calcolata. La media mobile viene calcolata a partire dal secondo punto. Se si specifica l'opzione **Inizia dal primo punto** , la media mobile verrà iniziata dal primo punto. Se è disponibile un unico punto dati, il punto nella media mobile calcolata sarà identico al primo punto della serie originale.  
  
## <a name="see-also"></a>Vedere anche  
* [Esercitazione: Aggiungere un istogramma al Report (Generatore Report)](Tutorial:%20Add%20a%20Column%20Chart%20to%20Your%20Report%20\(Report%20Builder\).md)
*  [Formattazione di un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
*  [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
*  [Aggiungere punti vuoti a un grafico &#40;Generatore Report e SSRS&#41;](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  
