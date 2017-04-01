---
title: "Stima delle dimensioni di una tabella | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pagine [SQL Server], spazio"
  - "spazio [SQL Server], tabelle"
  - "dimensioni di riga [SQL Server]"
  - "dimensioni [SQL Server], tabelle"
  - "dimensioni di colonna [SQL Server]"
  - "stima delle dimensioni di tabella [SQL Server]"
  - "dimensioni di tabella [SQL Server]"
  - "stima delle dimensioni di tabella"
  - "indici cluster, dimensioni tabella"
  - "spazio su disco [SQL Server], tabelle"
  - "allocazione spazio [SQL Server], dimensioni tabella"
  - "progettazione di database [SQL Server], stima delle dimensioni"
  - "righe libere riservate per pagina [SQL Server]"
  - "calcolo delle dimensioni di tabella"
ms.assetid: 15c17c92-616f-402e-894b-907a296efe5f
caps.latest.revision: 30
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 30
---
# Stima delle dimensioni di una tabella
  Per stimare la quantità di spazio necessario per archiviare dati in una tabella, è possibile utilizzare la procedura seguente:  
  
1.  Calcolare lo spazio necessario per l'heap o indice cluster seguendo le istruzioni in [Stima delle dimensioni di un heap](../../relational-databases/databases/estimate-the-size-of-a-heap.md) o [Stima delle dimensioni di un indice cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md).  
  
2.  Calcolare lo spazio necessario per ogni indice non cluster seguendo le istruzioni disponibili in [Stima delle dimensioni di un indice non cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md).  
  
3.  Sommare i valori calcolati nei passaggi 1 e 2.  
  
## Vedere anche  
 [Stima delle dimensioni di un database](../../relational-databases/databases/estimate-the-size-of-a-database.md)   
 [Stima delle dimensioni di un heap](../../relational-databases/databases/estimate-the-size-of-a-heap.md)   
 [Stima delle dimensioni di un indice cluster](../../relational-databases/databases/estimate-the-size-of-a-clustered-index.md)   
 [Stima delle dimensioni di un indice non cluster](../../relational-databases/databases/estimate-the-size-of-a-nonclustered-index.md)  
  
  