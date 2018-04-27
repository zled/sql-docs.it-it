---
title: Creare query UNION (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e00adf7e7c0611b9b2be2e102724949778bd5b42
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="create-union-queries-visual-database-tools"></a>Creare query UNION (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
La parola chiave UNION consente di includere i risultati di due istruzioni SELECT in una tabella risultante. Tutte le righe restituite dalle due istruzioni SELECT vengono combinate nel risultato dell'espressione UNION. Per gli esempi, vedere [Esempi di istruzioni SELECT (Transact-SQL)](http://msdn.microsoft.com/en-us/9b9caa3d-e7d0-42e1-b60b-a5572142186c).  
  
> [!NOTE]  
> Poiché nel riquadro Diagramma è possibile visualizzare solo una clausola SELECT, quando si lavora a una query di unione (query UNION), il Riquadro operazioni tabella verrà nascosto in Progettazione query.  
  
### <a name="to-create-a-merged-select-query"></a>Per creare una query SELECT unita  
  
1.  Aprire una query esistente o crearne una nuova.  
  
2.  Nel riquadro SQL digitare un'espressione UNION valida.  
  
    Nell'esempio seguente viene illustrata un'espressione UNION valida.  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  Per eseguire la query, scegliere **Esegui SQL** dal menu **Progettazione query** .  
  
    La query di unione verrà così formattata da Progettazione query.  
  
## <a name="see-also"></a>Vedere anche  
[Tipi di query supportati (Visual Database Tools)](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Procedure per la progettazione di query e viste (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Esecuzione di operazioni di base con le query (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[UNION (Transact-SQL)](http://msdn.microsoft.com/en-us/607c296f-8a6a-49bc-975a-b8d0c0914df7)  
  
