---
title: "Aggiungere una media mobile a un grafico (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
caps.latest.revision: 13
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Aggiungere una media mobile a un grafico (Generatore report e SSRS)
Una media mobile è una media dei dati della serie, calcolata in un periodo di tempo definito. Nei report impaginati [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è possibile indicare la media mobile sul grafico per identificare tendenze significative.  

![report-builder-column-chart-tutorial](../../reporting-services/media/report-builder-column-chart-tutorial.png)
  
 La formula della media mobile è l'indicatore di prezzo più diffuso utilizzato nelle analisi tecniche. Da una serie del grafico è anche possibile derivare molte altre formule, ad esempio media, mediana e deviazione standard. Quando si specifica una media mobile, ogni formula può includere uno o più parametri che devono essere specificati.  
  
 Quando si aggiunge una media mobile in modalità progettazione, la serie di linee aggiunta è solo un segnaposto visivo. I punti dati di ogni formula verranno calcolati durante l'elaborazione del report.  
  
 In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non è disponibile il supporto incorporato per le linee di tendenza.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Per aggiungere una media mobile calcolata in una serie del grafico  
  
1.  Fare clic con il pulsante destro del mouse in un campo dell'area **Valori** e scegliere **Aggiungi serie calcolata**. Verrà visualizzata la finestra di dialogo **Proprietà serie calcolata** .  
  
2.  Selezionare l'opzione **Media mobile** dall'elenco a discesa **Formula**.  
  
3.  Specificare un valore intero per **Periodo** , che rappresenta il periodo della media mobile.  
  
    > [!NOTE]  
    >  Il periodo è il numero di giorni utilizzato per calcolare una media mobile. Se sull'asse X non sono rappresentati valori di data/ora, il periodo è rappresentato dal numero di punti dati utilizzati per calcolare una media mobile. Se è disponibile un unico punto dati, la formula della media mobile non viene calcolata. La media mobile viene calcolata a partire dal secondo punto. Se si specifica l'opzione **Inizia dal primo punto** , la media mobile verrà iniziata dal primo punto. Se è disponibile un unico punto dati, il punto nella media mobile calcolata sarà identico al primo punto della serie originale.  
  
## Vedere anche  
 [Formattazione di un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Aggiungere punti vuoti a un grafico &#40;Generatore Report e SSRS&#41;](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  