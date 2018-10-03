---
title: Eliminare una tabella (SSAS tabulare) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: be4ed45f-fde3-466c-9869-49bd3ddb505e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 142a775415da489e67bc00b048651209a2a30179
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224761"
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
  
  
