---
title: Stimare le dimensioni di un tabella | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pages [SQL Server], space
- space [SQL Server], tables
- row size [SQL Server]
- size [SQL Server], tables
- column size [SQL Server]
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- disk space [SQL Server], tables
- space allocation [SQL Server], table size
- designing databases [SQL Server], estimating size
- reserved free rows per page [SQL Server]
- calculating table size
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 740800db335b524298c39a3ab9f225e18d785c54
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="estimate-the-size-of-a-table"></a>Stima delle dimensioni di una tabella
  Per stimare la quantità di spazio necessario per archiviare dati in una tabella, è possibile utilizzare la procedura seguente:  
  
1.  Calcolare lo spazio necessario per l'heap o indice cluster seguendo le istruzioni in [Stima delle dimensioni di un heap](../../relational-databases/databases/estimate-the-size-of-a-heap.md) o [Stima delle dimensioni di un indice cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md).  
  
2.  Calcolare lo spazio necessario per ogni indice non cluster seguendo le istruzioni disponibili in [Stima delle dimensioni di un indice non cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Sommare i valori calcolati nei passaggi 1 e 2.  
  
## <a name="see-also"></a>Vedere anche  
 [Stima delle dimensioni di un database](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [Stima delle dimensioni di un heap](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Stima delle dimensioni di un indice cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Stima delle dimensioni di un indice non cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  
