---
title: Creare alias di tabella (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a98f093964ae44dbb6bc301585d8a37e3bc3c296
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327021"
---
# <a name="create-table-aliases-visual-database-tools"></a>Creazione di alias di tabella (Visual Database Tools)
  Gli alias possono semplificare l'utilizzo dei nomi di tabella. L'utilizzo degli alias è utile se:  
  
-   Si intende abbreviare e rendere più facilmente leggibile l'istruzione nel [riquadro SQL](visual-database-tools.md) .  
  
-   Nella query si fa spesso riferimento al nome della tabella, ad esempio nei nomi che qualificano una colonna, e si desidera assicurarsi che venga rispettato un limite specifico per la lunghezza dei caratteri nella query. Alcuni database, infatti, impongono una lunghezza massima per le query.  
  
-   Si utilizzano più istanze della stessa tabella (come in un self-join) ed è necessario fare riferimento a un'istanza o un'altra.  
  
 È ad esempio possibile creare un alias `"e"` per un nome di tabella `employee`_`information`, quindi fare riferimento alla tabella con `"e"` in tutto il resto della query.  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a>Per creare un alias per una tabella o un oggetto con valori di tabella  
  
1.  Aggiungere alla query la tabella o l'oggetto con valori di tabella.  
  
2.  Nel **riquadro diagramma**fare clic con il pulsante destro del mouse sull'oggetto per cui si vuole creare un alias e scegliere **Proprietà** dal menu di scelta rapida.  
  
3.  Nella finestra **Proprietà** immettere l'alias nel campo **Alias** .  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere tabelle a query &#40;Visual Database Tools&#41;](add-tables-to-queries-visual-database-tools.md)   
 [Ordina e raggruppa i risultati della Query &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Riepilogo dei risultati di Query &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)   
 [Eseguire operazioni di base con le query &#40;Visual Database Tools&#41;](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
