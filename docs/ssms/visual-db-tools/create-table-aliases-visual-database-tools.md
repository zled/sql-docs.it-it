---
title: Creare alias di tabella (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d76ede0538ac5fb723e35fb32f045f3b14cd86ca
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="create-table-aliases-visual-database-tools"></a>Creazione di alias di tabella (Visual Database Tools)
Gli alias possono semplificare l'utilizzo dei nomi di tabella. L'utilizzo degli alias è utile se:  
  
-   Si intende abbreviare e rendere più facilmente leggibile l'istruzione nel [riquadro SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md) .  
  
-   Nella query si fa spesso riferimento al nome della tabella, ad esempio nei nomi che qualificano una colonna, e si desidera assicurarsi che venga rispettato un limite specifico per la lunghezza dei caratteri nella query. Alcuni database, infatti, impongono una lunghezza massima per le query.  
  
-   Si utilizzano più istanze della stessa tabella (come in un self-join) ed è necessario fare riferimento a un'istanza o un'altra.  
  
È ad esempio possibile creare un alias `"e"` per un nome di tabella `employee`_`information`, quindi fare riferimento alla tabella con `"e"` in tutto il resto della query.  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a>Per creare un alias per una tabella o un oggetto con valori di tabella  
  
1.  Aggiungere alla query la tabella o l'oggetto con valori di tabella.  
  
2.  Nel **riquadro diagramma**fare clic con il pulsante destro del mouse sull'oggetto per cui si vuole creare un alias e scegliere **Proprietà** dal menu di scelta rapida.  
  
3.  Nella finestra **Proprietà** immettere l'alias nel campo **Alias** .  
  
## <a name="see-also"></a>Vedere anche  
[Aggiunta di tabelle a query &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md)  
[Ordinare e raggruppare i risultati delle query &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Creare un riepilogo dei risultati di query &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Eseguire operazioni di base con le query &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

