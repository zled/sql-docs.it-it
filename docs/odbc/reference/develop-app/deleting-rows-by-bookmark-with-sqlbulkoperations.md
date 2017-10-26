---
title: L'eliminazione delle righe dal segnalibro con SQLBulkOperations | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: db7e04c5bf76855afdb24676c905c5cccbc60cbc
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>L'eliminazione delle righe dal segnalibro con SQLBulkOperations
Quando si elimina una riga dal segnalibro, **SQLBulkOperations** consente all'origine dati di eliminare uno o più righe selezionate della tabella. Le righe sono identificate mediante il segnalibro in una colonna del segnalibro associato.  
  
 Per eliminare righe dal segnalibro con **SQLBulkOperations**, l'applicazione esegue le operazioni seguenti:  
  
1.  Recupera e memorizza nella cache i segnalibri di tutte le righe da eliminare. Se è presente più di un segnalibro e viene utilizzata l'associazione per colonna, i segnalibri vengono archiviati in una matrice. Se è presente più di un segnalibro e viene utilizzata l'associazione per riga, i segnalibri vengono archiviati in una matrice di strutture di riga.  
  
2.  Imposta l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE sul numero di segnalibri e associa i buffer contenente il valore di segnalibro o la matrice dei segnalibri, alla colonna 0.  
  
3.  Chiamate **SQLBulkOperations** con *operazione* impostato su SQL_DELETE_BY_BOOKMARK.

