---
title: Creare query di eliminazione (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- row removal [SQL Server], Delete query
- Delete query
- queries [SQL Server], types
- removing rows
- removing data
- data deletions [SQL Server]
- deleting rows
- deleting data
ms.assetid: 0db3af43-1ec4-48c8-b769-2bb9c76d3434
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b96039bb192985375a2261ac339a3d9eaba01f6a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171350"
---
# <a name="create-delete-queries-visual-database-tools"></a>Creazione di query (Visual Database Tools)
  Per eliminare tutte le righe di una tabella, è possibile utilizzare una query di eliminazione.  
  
> [!NOTE]  
>  Se si eliminano tutte le righe di una tabella, non verrà eliminata la tabella, ma solo i dati in essa contenuti. Per eliminare una tabella da un database, fare clic su di essa con il pulsante destro del mouse in Esplora oggetti, quindi scegliere **Elimina**.  
  
 Quando si crea una query di eliminazione, nel riquadro Criteri vengono visualizzate le opzioni disponibili per l'eliminazione delle righe. Poiché la query di eliminazione non consente la visualizzazione di dati, vengono eliminate le colonne Output, Ordina per e Ordinamento. Vengono inoltre rimosse le caselle di controllo accanto ai nomi di colonna nel rettangolo che rappresenta la tabella o l'oggetto con valori di tabella, in quanto non è possibile specificare singole colonne da eliminare.  
  
 Se in Progettazione query e Progettazione viste non è possibile eliminare una o più righe, non ne verrà eliminata alcuna e un messaggio indicherà in quali righe sono contenute informazioni che non possono essere eliminate dal database.  
  
> [!CAUTION]  
>  Una volta eseguita, la query di eliminazione non potrà essere annullata. È dunque opportuno eseguire una copia di backup dei dati prima di eseguire la query di eliminazione.  
  
### <a name="to-create-a-delete-query"></a>Per creare una query di eliminazione  
  
1.  Aggiungere al riquadro Diagramma la tabella da cui eliminare le righe.  
  
2.  Scegliere **Modifica tipo** dal menu **Progettazione query**, quindi **Elimina**. **Nota** Se nel riquadro Diagramma sono visualizzate più tabelle quando si inizia a creare la query di eliminazione, in Progettazione query e Progettazione viste verrà visualizzata la finestra di dialogo [Elimina tabella](visual-database-tools.md) , in cui è necessario specificare il nome della tabella contenente le righe da eliminare.  
  
 Quando si esegue una query di eliminazione, non viene restituito alcun risultato nel [riquadro Risultati](results-pane-visual-database-tools.md). Viene invece visualizzato un messaggio che indica il numero di righe eliminate.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di Query supportati &#40;Visual Database Tools&#41;](supported-query-types-visual-database-tools.md)   
 [Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  