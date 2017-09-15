---
title: L'elaborazione delle istruzioni SQL | Documenti Microsoft
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
- ODBC cursor library [ODBC], statement processing
- SQL statements [ODBC], cursor library
- cursor library [ODBC], statement processing
ms.assetid: 54dad6a3-e86c-477b-ba7c-4e95e0385ec1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3613775e14453c2ed14e70cf122bd527217b2cd7
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="processing-sql-statements"></a>L'elaborazione delle istruzioni SQL
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 La libreria di cursori ODBC passa tutte le istruzioni SQL direttamente al driver ad eccezione dei seguenti:  
  
-   Aggiornamento posizionato e istruzioni delete  
  
-   **SELECT FOR UPDATE** istruzioni  
  
-   Istruzioni SQL in batch  
  
 Per eseguire l'aggiornamento posizionato e istruzioni delete e per posizionare il cursore su una riga per chiamare **SQLGetData** per tale riga, la libreria di cursori costruisce viene eseguita un'istruzione che identifica la riga.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Elaborazione posizionato istruzioni Update e Delete](../../../odbc/reference/appendixes/processing-positioned-update-and-delete-statements.md)  
  
-   [L'elaborazione di SELECT per le istruzioni UPDATE](../../../odbc/reference/appendixes/processing-select-for-update-statements.md)  
  
-   [Elaborazione batch di istruzioni SQL](../../../odbc/reference/appendixes/processing-batches-of-sql-statements.md)  
  
-   [Costruzione di istruzioni di ricerca](../../../odbc/reference/appendixes/constructing-searched-statements.md)
