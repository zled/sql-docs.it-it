---
title: Aggiungere un gruppo dettagli (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 552ba371480589a72e4c581641909f4e8fe9577c
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="add-a-details-group-report-builder-and-ssrs"></a>Aggiungere un gruppo dettagli (Generatore report e SSRS)
In un report impaginato di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , i dati dettaglio di un set di dati del report vengono specificati come gruppo senza espressione di raggruppamento. È possibile aggiungere un gruppo dettagli a un'area dati Tablix esistente quando si desidera visualizzare i dati dettaglio per una matrice, aggiungere di nuovo i dati dettaglio eliminati da una tabella o un elenco oppure aggiungere ulteriori gruppi dettagli. Per altre informazioni sui gruppi, vedere [Informazioni sui gruppi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-details-group-to-a-tablix-data-region"></a>Per aggiungere un gruppo dettagli a un'area dati Tablix  
  
1.  Nell'area di progettazione fare clic in un punto qualsiasi nell'area dati Tablix per selezionarla. Nel riquadro di raggruppamento vengono visualizzati i gruppi di righe e colonne per l'area dati selezionata.  
  
2.  Nel riquadro di raggruppamento fare clic con il pulsante destro del mouse su un gruppo che rappresenta il gruppo figlio più interno. Scegliere **Aggiungi gruppo**, quindi fare clic su **Gruppo figlio**. Verrà visualizzata la finestra di dialogo **Gruppo Tablix** .  
  
3.  In **Espressione di raggruppamento**lasciare vuota l'espressione. In un gruppo dettagli non è presente alcuna espressione.  
  
4.  Selezionare **Mostra dati dettaglio**.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Un nuovo gruppo dettagli verrà aggiunto come gruppo figlio nel riquadro di raggruppamento e nell'handle di riga per il gruppo selezionato al passaggio 1 verrà visualizzata l'icona del gruppo dettagli. Per altre informazioni sugli handle, vedere [Celle, righe e colonne dell'area dati Tablix &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere o eliminare un gruppo in un'area dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)   
 [Informazioni sui gruppi &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md)   
 [Area dati Tablix &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Tabelle &#40; Generatore report e SSRS &#41; ](../../reporting-services/report-design/tables-report-builder-and-ssrs.md) [Matrici &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [Gli elenchi di &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)      
 [Tabelle, matrici e gli elenchi di &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  

