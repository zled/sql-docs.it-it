---
title: Strumenti di progettazione di query e viste (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.querydesigner
- vdt.pane.diagram
- vdt.pane.grid
- vdt.dlgbox.querybuilder
- vdt.pane.sql
- vdt.pane.results
helpviewer_keywords:
- Query Designer [SQL Server], panes
- View Designer, panes
- Query Designer [SQL Server], components
- View Designer, components
ms.assetid: 12e4b5a5-b793-4b6c-a0e5-c450c49bf26f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 45b05e606f083b20fa7b1ba9e8a25b4defcf7c7c
ms.lasthandoff: 04/11/2017

---
# <a name="query-and-view-designer-tools-visual-database-tools"></a>Strumenti di progettazione di query e viste (Visual Database Tools)
Quando si progetta una query, una vista, una funzione inline o una stored procedure a istruzione singola, la finestra di progettazione utilizzata è costituita da quattro riquadri: Diagramma, Criteri, SQL e Risultati.  
  
![Progettazione query](../../ssms/visual-db-tools/media/vs_queryviewdsgpanes.gif "Progettazione query")  
  
-   Il riquadro Diagramma visualizza le tabelle e gli altri oggetti con valori di tabella su cui si esegue la query. Ogni rettangolo rappresenta una tabella o un oggetto con valori di tabella e visualizza le colonne di dati disponibili. I join sono indicati da linee fra i rettangoli. Per altre informazioni, vedere [Riquadro Diagramma &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md).  
  
-   Il riquadro Criteri contiene una griglia simile a un foglio di calcolo in cui è possibile specificare varie opzioni, ad esempio le colonne di dati da visualizzare, le righe da selezionare, come raggruppare le righe e così via. Per altre informazioni, vedere [Riquadro Criteri &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md).  
  
-   Il riquadro SQL riporta l'istruzione SQL della query o della vista. È possibile modificare l'istruzione SQL creata da Progettazione query oppure immettere un'istruzione SQL personalizzata. Questo riquadro risulta particolarmente utile per l'immissione di istruzioni SQL che non è possibile creare con i riquadri Diagramma e Criteri, come nel caso delle query di unione. Per altre informazioni, vedere [Riquadro SQL &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
-   Il riquadro Risultati visualizza una griglia contenente i dati recuperati dalla query o dalla vista. In Progettazione query e Progettazione viste questo riquadro visualizza i risultati dell'ultima query SELECT eseguita. È possibile modificare il database cambiando i valori nelle celle della griglia e aggiungere o eliminare righe. Per altre informazioni, vedere [Riquadro Risultati &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/results-pane-visual-database-tools.md).  
  
Le query o le viste possono essere create in qualsiasi riquadro: è possibile specificare una colonna da visualizzare scegliendola nel riquadro Diagramma, immettendola nel riquadro Criteri o inserendola nell'istruzione SQL del riquadro SQL.  
  
## <a name="displaying-and-hiding-panes"></a>Visualizzare e nascondere riquadri  
Per nascondere un riquadro o visualizzarne uno non visibile, fare clic con il pulsante destro del mouse nell'area di progettazione, scegliere **Riquadro**e fare clic sul nome del riquadro. Se Progettazione query e Progettazione viste è aperto in modalità Progettazione query, il riquadro **Risultati** non è disponibile.  
  
## <a name="see-also"></a>Vedere anche  
[Procedure per la progettazione di query e viste &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Aprire Progettazione query e Progettazione viste &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/open-the-query-and-view-designer-visual-database-tools.md)  
[Editor SQL &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/sql-editor-visual-database-tools.md)  
  
