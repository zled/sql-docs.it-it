---
title: Eliminare relazioni (SSAS tabulare) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: multidimensional-tabular
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d40e3f05-54e8-4c4b-807a-0b06f446079b
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 54f2d9205ec7e8815572e9107e6319262c343edd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="delete-relationships-ssas-tabular"></a>Eliminare relazioni (SSAS tabulare)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]È possibile eliminare le relazioni esistenti utilizzando Progettazione modelli in vista diagramma o nella finestra di dialogo Gestisci relazioni. Per informazioni sulla modalità d'uso delle relazioni nei modelli tabulari, vedere [Relazioni &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/relationships-ssas-tabular.md).  
  
## <a name="considerations-for-deleting-relationships"></a>Considerazioni sull'eliminazione di relazioni  
 Quando si decide se eliminare una relazione, tenere presente i fattori seguenti:  
  
-   L'eliminazione di una relazione non può essere annullata in alcun modo. È possibile creare nuovamente la relazione, tuttavia questa azione richiede un ricalcolo completo delle formule nel modello. Eseguire pertanto sempre un controllo prima di eliminare una relazione utilizzata nelle formule.  
  
-   L'eliminazione di una relazione tra due tabelle può provocare errori nelle formule che fanno riferimento a queste tabelle.  
  
-   La funzione Data Analysis Expression (DAX) RELATED consente di utilizzare le relazioni tra tabelle per cercare valori correlati in un'altra tabella e, dopo l'eliminazione della relazione, verranno restituiti valori diversi. Per ulteriori informazioni, vedere la funzione RELATED (DAX).  
  
-   Oltre a cambiare i risultati delle formule e delle tabelle pivot, sia la creazione sia l'eliminazione delle relazioni determinano il ricalcolo della cartella di lavoro, operazione che può richiedere tempo.  
  
## <a name="delete-relationships"></a>Eliminare relazioni  
  
#### <a name="to-delete-a-relationship-by-using-diagram-view"></a>Per eliminare una relazione tramite Vista diagramma  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]scegliere **Vista modelli** dal menu **Modello**, quindi fare clic su **Vista diagramma**.  
  
2.  Fare clic con il pulsante destro del mouse su una linea della relazione tra le due tabelle, quindi scegliere **Elimina**.  
  
#### <a name="to-delete-a-relationship-by-using-the-manage-relationships-dialog-box"></a>Per eliminare una relazione utilizzando la finestra di dialogo Gestisci relazioni  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]scegliere **Gestisci relazioni** dal menu **Tabella**.  
  
2.  Nella finestra di dialogo **Gestisci relazioni** selezionare una o più relazioni dall'elenco.  
  
     Per selezionare più relazioni, tenere premuto CTRL mentre si fa clic su ciascuna relazione.  
  
3.  Fare clic su **Elimina relazione**.  
  
4.  Fare clic su **Chiudi** nella finestra di dialogo **Gestisci relazioni**.  
  
## <a name="see-also"></a>Vedere anche  
 [Relazioni &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/relationships-ssas-tabular.md)   
 [Creare una relazione tra due tabelle &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md)  
  
  
