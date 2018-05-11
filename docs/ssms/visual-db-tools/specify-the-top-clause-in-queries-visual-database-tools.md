---
title: Definire la clausola TOP nelle query (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
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
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1bcf376898866238839c0658d9b445e11b05c70e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="specify-the-top-clause-in-queries-visual-database-tools"></a>Definire la clausola TOP nelle query (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
> Per modificare i valori delle proprietà figlio della proprietà **Specifica Top** , è anche possibile modificare la clausola TOP nel riquadro SQL.  
  
## <a name="see-also"></a>Vedere anche  
[Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Proprietà delle query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-properties-visual-database-tools.md)  
  
