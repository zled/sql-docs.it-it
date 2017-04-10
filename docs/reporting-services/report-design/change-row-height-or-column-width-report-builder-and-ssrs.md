---
title: "Modificare l&#39;altezza di riga o la larghezza di colonna (Generatore report e SSRS) | Microsoft Docs"
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
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Modificare l&#39;altezza di riga o la larghezza di colonna (Generatore report e SSRS)
  Quando si imposta un'altezza di riga, si specifica l'altezza massima della riga nel report visualizzabile. Per impostazione predefinita, tuttavia, le caselle di testo nella riga sono impostate in modo da ingrandirsi verticalmente per poter contenere i dati immessi in fase di esecuzione. Per questo motivo, può verificarsi che una riga si espanda oltre l'altezza specificata dall'utente. Per impostare un'altezza di riga fissa è necessario modificare le proprietà della casella di testo in modo che non venga espansa automaticamente.  
  
 Quando si imposta una larghezza di colonna, si specifica la larghezza massima della colonna nel report visualizzabile. Le colonne non si espandono automaticamente in senso orizzontale in base al testo.  
  
 Se una cella in una riga o in una colonna contiene un rettangolo o un'area dati, l'altezza e la larghezza minima della cella vengono determinate in base all'altezza e alla larghezza dell'elemento contenuto. Per altre informazioni, vedere [Tipi di rendering  &#40;Generatore report e SSRS &#41;](../../reporting-services/report-design/rendering-behaviors-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Per modificare l'altezza delle righe spostando gli handle di riga  
  
1.  In visualizzazione della struttura fare clic in un punto qualsiasi dell'area dati Tablix per selezionarla. Lungo il bordo esterno dell'area dati Tablix vengono visualizzati alcuni handle di riga grigi.  
  
2.  Passare con il puntatore del mouse sul bordo dell'handle di riga che si desidera espandere. Verrà visualizzata una freccia doppia.  
  
3.  Fare clic per selezionare il bordo della riga e spostarlo più in alto o più in basso per regolare l'altezza della riga.  
  
### Per modificare l'altezza delle righe impostando le proprietà delle celle  
  
1.  In visualizzazione Progettazione fare clic su una cella nella riga di tabella.  
  
     ![Cella selezionata in una tabella](../../reporting-services/report-design/media/table-selectcell.png "Cella selezionata in una tabella")  
  
2.  Nel riquadro **Proprietà** visualizzato modificare la proprietà **Altezza**, quindi fare clic in un punto qualsiasi all'esterno del riquadro **Proprietà**.  
  
     ![Riquadro Proprietà della cella di tabella selezionata](../../reporting-services/report-design/media/cell-propertiespane.png "Riquadro Proprietà della cella di tabella selezionata")  
  
### Per impedire che una riga si espanda automaticamente in senso verticale  
  
1.  In visualizzazione della struttura fare clic in un punto qualsiasi dell'area dati Tablix per selezionarla. Lungo il bordo esterno dell'area dati Tablix vengono visualizzati alcuni handle di riga grigi.  
  
2.  Fare clic sull'handle di riga per selezionare la riga.  
  
3.  Nel riquadro Proprietà impostare CanGrow su **False**.  
  
    > [!NOTE]  
    >  Se non viene visualizzato il riquadro Proprietà, scegliere **Proprietà** dal menu **Visualizza**.  
  
### Per modificare la larghezza delle colonne  
  
1.  In visualizzazione della struttura fare clic in un punto qualsiasi dell'area dati Tablix per selezionarla. Lungo il bordo esterno dell'area dati Tablix vengono visualizzati alcuni handle di colonna grigi.  
  
2.  Passare con il puntatore del mouse sul bordo dell'handle di colonna che si desidera espandere. Verrà visualizzata una freccia doppia.  
  
3.  Fare clic per selezionare il bordo della colonna e spostarlo verso sinistra o verso destra per regolare la larghezza della colonna.  
  
## Vedere anche  
 [Area dati Tablix (Generatore report e SSRS)](https://msdn.microsoft.com/library/dd220587.aspx)   
 [Celle, righe e colonne dell'area dati Tablix (Generatore report e SSRS)](https://msdn.microsoft.com/library/dd220511.aspx)   
 [Tabelle (Generatore report e SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [Matrici (Generatore report e SSRS)](https://msdn.microsoft.com/library/dd207149.aspx)   
 [Elenchi (Generatore report e SSRS)](https://msdn.microsoft.com/library/dd239330.aspx)   
 [Tabelle, matrici ed elenchi (Generatore report e SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  