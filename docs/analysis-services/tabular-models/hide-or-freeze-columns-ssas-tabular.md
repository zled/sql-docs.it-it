---
title: Nascondere o bloccare colonne | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 05503ab615b5f22bfd8a6dfd94144648659d4a26
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="hide-or-freeze-columns"></a>Nascondere o bloccare colonne 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
In Progettazione modelli, se in una tabella sono presenti colonne che non si desidera visualizzare, è possibile nasconderle temporaneamente. Nascondendo una colonna si ottiene maggiore spazio sullo schermo per aggiungerne di nuove o per utilizzare solo le colonne di dati rilevanti. È possibile nascondere e scoprire colonne dal menu **Colonna** in Progettazione modelli e dal menu di scelta rapida disponibile in ogni intestazione di colonna. Per mantenere visibile un'area di un modello durante lo scorrimento a un'altra area del modello, è possibile bloccare colonne specifiche in un'area.  
  
> [!IMPORTANT]  
>  La possibilità di nascondere colonne non dovrebbe essere utilizzata per la sicurezza dei dati, ma solo per semplificare e abbreviare l'elenco di colonne visibili in Progettazione modelli o nei report. Per proteggere i dati, è possibile definire ruoli di sicurezza. I ruoli possono limitare la visualizzazione di metadati e dati in base agli oggetti definiti nel ruolo. Per ulteriori informazioni, vedere [ruoli](../../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
 Quando si nasconde una colonna, è possibile scegliere se nasconderla mentre si lavora in Progettazione modelli o nei report. Se si nascondono tutte le colonne, l'intera tabella appare vuota in Progettazione modelli.  
  
> [!NOTE]  
>  Se sono molte le colonne da nascondere, è possibile creare una prospettiva anziché nascondere e scoprire colonne. Una prospettiva è una vista personalizzata dei dati tramite cui si semplifica l'utilizzo di un subset di dati correlati. Per ulteriori informazioni, vedere [crea e Gestisci prospettive](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)  
  
### <a name="to-hide-an-individual-column"></a>Per nascondere una singola colonna  
  
1.  In Progettazione modelli selezionare la tabella contenente la colonna che si desidera nascondere.  
  
2.  Fare clic con il pulsante destro del mouse sulla colonna, selezionare **Nascondi colonne**, quindi fare clic su **Da finestra progettazione e report**, **Da report**oppure su **Da finestra di progettazione**.  
  
### <a name="to-hide-multiple-columns"></a>Per nascondere più colonne  
  
1.  In Progettazione modelli selezionare la tabella contenente le colonne che si desidera nascondere.  
  
2.  Fare clic sul menu **Colonne** , quindi scegliere **Nascondi e scopri**.  
  
3.  Nella finestra di dialogo **Nascondi e scopri colonne** individuare ogni colonna che si desidera nascondere, quindi deselezionare una o entrambe le opzioni **In Designer** (Nella finestra di progettazione) e **In Reports**(Nei report).  
  
4.  Scegliere **OK**.  
  
### <a name="to-freeze-columns"></a>Per bloccare le colonne  
  
1.  In Progettazione modelli selezionare la tabella contenente le colonne che si desidera bloccare.  
  
2.  Selezionare una o più colonne da bloccare.  
  
3.  Fare clic sul menu **Colonne** , quindi scegliere **Blocca**.  
  
    > [!NOTE]  
    >  Quando una colonna viene bloccata, viene spostata a sinistra della tabella (o davanti) nella finestra di progettazione. Se sbloccata, la colonna non torna nella relativa posizione originale.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e colonne](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)   
 [Prospettive](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
