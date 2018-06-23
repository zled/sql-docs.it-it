---
title: Visualizzare dati spaziali in Esplora oggetti | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9ad57fb492b58c26ace1389ce217fda2e78b542a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157969"
---
# <a name="view-spatial-data-in-object-explorer"></a>Visualizzazione di dati spaziali in Esplora oggetti
  La finestra **Risultati spaziali** dell'editor di query fornisce strumenti di mapping visivo per la visualizzazione di risultati di dati spaziali in aggiunta alla visualizzazione dei dati in formato griglia nella finestra **Risultati** . Per visualizzare i dati spaziali nella finestra **Risultati spaziali** , i risultati delle query devono contenere almeno una colonna di dati spaziali con dati geometrici e geografici.  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>Per visualizzare i dati spaziali nella finestra Risultati spaziali  
  
1.  Nell'editor di query fare clic sulla scheda **Risultati spaziali** .  
  
    > [!NOTE]  
    >  Questa finestra non è disponibile se i risultati delle query non contengono dati spaziali o si richiede la restituzione dei risultati come testo.  
  
2.  Selezionare la colonna che si desidera visualizzare nell'elenco **Selezionare la colonna spaziale** . Se la tabella contiene una sola colonna spaziale, questa sarà l'opzione predefinita dell'elenco.  
  
3.  Selezionare la colonna non spaziale che si vuole usare come etichette dei dati nell'elenco **Selezionare la colonna etichetta** .  
  
4.  Selezionare la proiezione desiderata per i dati geografici nell'elenco **Selezionare la proiezione** . La proiezione predefinita è Equirectangular. Le altre proiezioni disponibili sono Mercator, Robinson e Bonne.  
  
    > [!NOTE]  
    >  **Selezionare la proiezione** non è disponibile se la colonna spaziale contiene dati geometrici.  
  
5.  Regolare il dispositivo di scorrimento **Zoom** per aumentare la dimensione visiva degli elementi di cui è stato eseguito il mapping. Per le forme poligonali, l'etichetta è visibile solo se la forma è grande abbastanza da contenere il testo dell'etichetta.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra Risultati spaziali](spatial-results-window.md)   
 [Editor di query del motore di database &#40;SQL Server Management Studio&#41;](database-engine-query-editor-sql-server-management-studio.md)   
 [Editor di query e di testo &#40;SQL Server Management Studio&#41;](query-and-text-editors-sql-server-management-studio.md)  
  
  