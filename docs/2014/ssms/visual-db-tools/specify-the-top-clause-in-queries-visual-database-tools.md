---
title: Definire la clausola TOP nelle query (Visual Database Tools) | Microsoft Docs
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
- TOP clause, queries
- percentage of rows returned [SQL Server]
- number of rows
- search conditions [SQL Server], TOP clause
- restricting rows returned
- search criteria [SQL Server], limiting rows returned
- inspecting portion of results
- limiting rows returned
- search criteria [SQL Server], TOP clause
ms.assetid: ba7d7c10-9bb3-4d9b-90b0-5fa94ecae59b
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1726f0c0ba83e689a0f09dc9e6f64d4175302b36
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327001"
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a>Definire la clausola TOP nelle query (Visual Database Tools)
  La clausola TOP restituisce solo le prime *n* righe o il primo *n percento* delle righe di una query. La clausola TOP è utile quando si desidera controllare una parte dei risultati per verificare se la query funziona come previsto. Tale clausola consente di eseguire questa operazione senza occupare tutte le risorse necessarie per restituire tutti i risultati della query.  
  
### <a name="to-specify-the-top-clause-in-queries"></a>Per specificare la clausola TOP nelle query  
  
1.  Aprire una query in Esplora soluzioni o crearne una nuova.  
  
2.  Scegliere **Finestra Proprietà** dal menu **Visualizza**.  
  
3.  Nella finestra **Proprietà**individuare ed espandere la proprietà **Specifica Top** .  
  
4.  Fare clic sulla proprietà figlio **(Top)** e impostarla su **Sì**.  
  
5.  Nella proprietà figlio **Espressione** digitare un'espressione con risultato numerico, ad esempio "10" o "2*5".  
  
6.  Fare clic sulla proprietà figlio **Percentuale** e indicare se la proprietà **Espressione** deve essere considerata come percentuale di tutte le righe restituite (Sì) o come numero assoluto di righe restituite (No).  
  
7.  Se nella query viene usata la clausola ORDER BY, fare clic sulla proprietà figlio **Con valori equivalenti** e scegliere **Sì** per visualizzare tutte le righe di un gruppo se viene inclusa solo una parte del gruppo oppure **No** per non visualizzarle tutte.  
  
 Man mano che si esegue la procedura sopra descritta, la clausola TOP visualizzata nel riquadro SQL viene aggiornata in base alle impostazioni correnti delle proprietà.  
  
> [!NOTE]  
>  Per modificare i valori delle proprietà figlio della proprietà **Specifica Top** , è anche possibile modificare la clausola TOP nel riquadro SQL.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure per le query e visualizzazioni di progettazione &#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [Proprietà delle query &#40;Visual Database Tools&#41;](query-properties-visual-database-tools.md)  
  
  
