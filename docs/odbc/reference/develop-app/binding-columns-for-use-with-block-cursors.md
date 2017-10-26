---
title: Associazione delle colonne per l'utilizzo con i cursori a blocchi | Documenti Microsoft
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
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fe8c88946d6602f77bc39ac03b280fcca99cb8de
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="binding-columns-for-use-with-block-cursors"></a>Associazione delle colonne per l'utilizzo con i cursori a blocchi
Poiché i cursori a blocchi restituiscano più righe, le applicazioni che li utilizzano devono associare una matrice di variabili per ogni colonna anziché una singola variabile. Queste matrici sono noti come il *buffer rowset*. Di seguito sono due stili di associazione.  
  
-   Associare una matrice per ogni colonna. Si tratta di *associazione per colonna* perché ogni struttura di dati (matrice) contiene dati per una singola colonna.  
  
-   Definire una struttura per contenere i dati per un'intera riga e associare una matrice di strutture. Si tratta di *l'associazione per riga* perché ogni struttura di dati contiene i dati per una singola riga.  
  
 Quando l'applicazione associa le variabili sola alle colonne, che chiama **SQLBindCol** per associare le matrici a colonne. L'unica differenza è che gli indirizzi passati sono gli indirizzi di matrice, non solo indirizzi di variabili. L'applicazione imposta l'attributo di istruzione SQL_BIND_BY_COLUMN per specificare se utilizza l'associazione per colonna o per riga. Se si desidera utilizzare l'associazione per colonna o per riga consiste in gran parte delle preferenze di applicazione. L'associazione potrebbe corrispondere più da vicino al layout dell'applicazione di dati, nel qual caso fornisce prestazioni migliori.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [L'associazione per colonna](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [L'associazione per riga](../../../odbc/reference/develop-app/row-wise-binding.md)

