---
title: Stimare le dimensioni di un tabella | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 76f650bbfccba0eef9b269791605ae9a76235494
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37250181"
---
# <a name="estimate-the-size-of-a-table"></a>Stima delle dimensioni di una tabella
  Per stimare la quantità di spazio necessario per archiviare dati in una tabella, è possibile utilizzare la procedura seguente:  
  
1.  Calcolare lo spazio necessario per l'heap o indice cluster seguendo le istruzioni in [Stima delle dimensioni di un heap](estimate-the-size-of-a-heap.md) o [Stima delle dimensioni di un indice cluster](estimate-the-size-of-a-clustered-index.md).  
  
2.  Calcolare lo spazio necessario per ogni indice non cluster seguendo le istruzioni disponibili in [Stima delle dimensioni di un indice non cluster](estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Sommare i valori calcolati nei passaggi 1 e 2.  
  
## <a name="see-also"></a>Vedere anche  
 [Stima delle dimensioni di un database](estimate-the-size-of-a-database.md)   
 [Stima delle dimensioni di un heap](estimate-the-size-of-a-heap.md)   
 [Stima delle dimensioni di un indice cluster](estimate-the-size-of-a-clustered-index.md)   
 [Stima delle dimensioni di un indice non cluster](estimate-the-size-of-a-nonclustered-index.md)  
  
  
