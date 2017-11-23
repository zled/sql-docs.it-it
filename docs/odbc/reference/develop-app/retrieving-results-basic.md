---
title: Il recupero dei risultati (Basic) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], about result sets
- data sources [ODBC], result sets
- empty result sets [ODBC]
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 54a310e3e2f13431c0963f513fb9d5c4ec4e226b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="retrieving-results-basic"></a>Il recupero dei risultati (Basic)
Oggetto *set di risultati* è un set di righe nell'origine dati che soddisfa determinati criteri. È una tabella concettuale che nei risultati di una query e che sia disponibile per un'applicazione in formato tabulare. **Selezionare** istruzioni, funzioni di catalogo e alcune procedure creano set di risultati. Nell'esempio seguente, la prima istruzione SQL crea un set di risultati contenente tutte le righe e tutte le colonne nella tabella Orders e la seconda istruzione SQL crea un set di risultati contenente le colonne OrderID, venditore e stato per le righe nella tabella Orders in cui lo stato è aperto:  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 Un set di risultati può essere vuoto, che è diverso da alcun risultato impostato. Ad esempio, l'istruzione SQL seguente crea un set di risultati vuoto:  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 Un set di risultati vuoto non è diverso da qualsiasi altro set di risultati ad eccezione del fatto che non contiene righe. Ad esempio, l'applicazione può recuperare i metadati per il set di risultati, può tentare di recuperare le righe e deve chiudere il cursore sul set di risultati.  
  
 Viene chiamato il processo di recupero di righe dall'origine dati e restituirli all'applicazione *recupero*. Questa sezione illustra le parti fondamentali del processo. Per ulteriori informazioni sugli argomenti più avanzati, ad esempio blocco e i cursori scorrevoli, vedere [cursori a blocchi](../../../odbc/reference/develop-app/block-cursors.md) e [cursori scorrevoli](../../../odbc/reference/develop-app/scrollable-cursors.md). Per informazioni sull'aggiornamento, eliminazione e inserimento di righe, vedere [Panoramica di aggiornamento dati](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [È stato creato un set di risultati?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [Metadati del set di risultati](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [Associazione di colonne](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [Recupero di dati](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [Chiusura del cursore](../../../odbc/reference/develop-app/closing-the-cursor.md)
