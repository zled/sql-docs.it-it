---
title: Eliminare una tabella (SSAS tabulare) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: be456ceeef0d8d965c9e922bffbcec0507cb3777
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="delete-a-table-ssas-tabular"></a>Eliminare una tabella (SSAS tabulare)
  In Progettazione modelli è possibile eliminare le tabelle non più necessarie nel database dell'area di lavoro modello. L'eliminazione di una tabella non influisce sui dati di origine, ma solo sui dati importati che si stavano utilizzando. Non è possibile annullare l'eliminazione di una tabella.  
  
### <a name="to-delete-a-table"></a>Per eliminare una tabella  
  
-   Fare clic con il pulsante destro del mouse sulla scheda nella parte inferiore di Progettazione modelli per la tabella che si vuole eliminare, quindi scegliere **Elimina**.  
  
## <a name="considerations-when-deleting-tables"></a>Considerazioni in caso di eliminazione di tabelle  
  
-   Quando si elimina una tabella, viene eliminata la scheda intera nella quale si trova la tabella.  
  
-   Se tutte le misura sono associate a tale tabella, anche la definizione della misura sarà eliminata.  
  
-   Se sono state create alcune colonne calcolate utilizzando quella tabella, anche le colonne in tale tabella vengono eliminate. Nelle colonne calcolate delle altre tabelle in cui vengono utilizzate colonne della tabella eliminata verrà visualizzato un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e colonne &#40;SSAS tabulare&#41;](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)  
  
  
