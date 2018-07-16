---
title: Eliminare una tabella (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
caps.latest.revision: 8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e57cdddbbd7cc4ee75c0758b84d6a68b7fadfd6b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37308491"
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
 [Tabelle e colonne &#40;tabulare di SSAS&#41;](tables-and-columns-ssas-tabular.md)  
  
  
