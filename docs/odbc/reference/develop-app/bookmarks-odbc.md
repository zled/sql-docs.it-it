---
title: I segnalibri (ODBC) | Documenti Microsoft
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
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 791350c93e2570ad8615e5b378e9979870e02acf
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="bookmarks-odbc"></a>Segnalibri (ODBC)
Un segnalibro è un valore utilizzato per identificare una riga di dati. Il significato del valore del segnalibro è noto solo al driver o all'origine dati. Un segnalibro, ad esempio, può essere tanto semplice quanto un numero di riga o tanto complesso quanto un indirizzo del disco. I segnalibri in ODBC sono leggermente diversi dai segnalibri nella documentazione reale. Un libro reale, il lettore inserisce un segnalibro in una pagina specifica e quindi cerca il segnalibro tornare alla pagina. In ODBC l'applicazione richiede un segnalibro per una determinata riga, lo archivia e lo passa nuovamente al cursore per tornare alla riga. Pertanto, i segnalibri in ODBC sono simili a un lettore di scrittura di un numero di pagina, ricordare e quindi cercare nuovamente la pagina.  
  
 Per determinare il supporto di un driver di segnalibri, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_BOOKMARK_PERSISTENCE. Il bit di questo valore viene descritto cosa segnalibri operazioni sopravvivono, ad esempio se i segnalibri sono ancora validi dopo il cursore è chiuso.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Tipi di segnalibro](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [Il recupero dei segnalibri](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [Lo scorrimento in base al segnalibro](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [L'aggiornamento, eliminazione o recupero dal segnalibro](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [Confronto tra i segnalibri](../../../odbc/reference/develop-app/comparing-bookmarks.md)
