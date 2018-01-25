---
title: Riepilogare o aggregare valori mediante espressioni personalizzate | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- summarizing query results
- custom expressions to aggregate values [SQL Server]
ms.assetid: 34130ac1-0106-4766-b324-acb0b7bb6f6e
caps.latest.revision: "3"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5506c43d001a1d02e081d19696b34be2e9c1f4ba
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="summarize-or-aggregate-values-using-custom-expressions-visual-database-tools"></a>Riepilogo o aggregazione di valori mediante l'utilizzo di espressioni personalizzate (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Oltre a usare le funzioni di aggregazione per raggruppare i dati, è possibile creare espressioni personalizzate che producono valori aggregati. È possibile utilizzare espressioni personalizzate al posto di funzioni di aggregazione in qualsiasi punto di una query di aggregazione.  
  
Si supponga ad esempio che nella tabella `titles` si desideri creare una query in cui sia riportato non solo il prezzo medio ma anche il prezzo medio dopo l'applicazione di uno sconto.  
  
In questo caso non sarà possibile includere un'espressione basata su calcoli che coinvolgono solo singole righe della tabella; l'espressione dovrà essere basata su un valore aggregato in quanto al momento del calcolo dell'espressione sono disponibili solo i valori aggregati.  
  
### <a name="to-specify-a-custom-expression-for-a-summary-value"></a>Per specificare un'espressione personalizzata per un valore di riepilogo  
  
1.  Specificare i gruppi per la query. Per informazioni dettagliate, vedere [Raggruppare righe nei risultati di una query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/group-rows-in-query-results-visual-database-tools.md).  
  
2.  Spostarsi su una riga vuota del riquadro Criteri e digitare l'espressione nella colonna **Columns**.  
  
    In [Progettazione query e Progettazione viste](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) verrà assegnato automaticamente all'espressione un alias di colonna in modo da creare un'intestazione di colonna utile nell'output della query. Per altre informazioni dettagliate, vedere [Creazione di alias di colonna &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/create-column-aliases-visual-database-tools.md).  
  
3.  Nella colonna **Group By** per l'espressione selezionare **Espressione**.  
  
4.  Consente di eseguire la query.  
  
## <a name="see-also"></a>Vedere anche  
[Ordinare e raggruppare i risultati delle query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Creare un riepilogo dei risultati di query &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
  
