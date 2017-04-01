---
title: "Traccia di dati su un asse secondario (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Traccia di dati su un asse secondario (Generatore report e SSRS)
  Nel grafico sono inclusi due tipi di asse: principale e secondario. L'asse secondario risulta utile quando si confrontano due set di valori con due intervalli di dati diversi che condividono una categoria comune.  
  
 Si supponga ad esempio che in un grafico vengano calcolati i valori relativi ai ricavi rispetto alle imposte nell'anno 2008. In questo caso, il periodo di tempo 2008 è comune a entrambi i set di valori. Tuttavia, quando le due serie vengono tracciate sullo stesso asse Y, non è possibile effettuare un confronto utile, perché la scala di quest'asse è ottimizzata per i valori maggiori nel set di dati. Indicando i ricavi sull'asse principale e le imposte su quello secondario, è possibile visualizzare ogni serie su un proprio asse Y con una scala di valori specifica. Le serie condividono un asse X comune.  
  
 Nelle situazioni in cui è necessario confrontare più di due serie, è consigliabile un approccio diverso per il confronto e la visualizzazione di più serie in un grafico. Per altre informazioni, vedere [Più serie in un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md).  
  
 Un esempio di questo grafico è disponibile come report di esempio. Per altre informazioni sul download di questo e di altri report di esempio, vedere la pagina relativa ai [report di esempio per Generatore report e Progettazione report](http://go.microsoft.com/fwlink/?LinkId=198283) di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Per tracciare una serie sull'asse secondario  
  
1.  Fare clic con il pulsante destro del mouse sulla serie nel grafico oppure in un campo dell'area **Valori** che si vuole visualizzare sull'asse secondario, quindi scegliere **Proprietà serie**. Verrà visualizzata la finestra di dialogo **Proprietà serie** .  
  
2.  Fare clic su **Assi e area grafico**, quindi selezionare quale degli assi secondari si desidera abilitare, l'asse dei valori o l'asse delle categorie.  
  
## Vedere anche  
 [Formattazione delle etichette degli assi in un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Specificare un intervallo dell'asse &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)  
  
  