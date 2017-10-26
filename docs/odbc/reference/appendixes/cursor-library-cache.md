---
title: Cursore libreria Cache | Documenti Microsoft
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
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 06b893a857f87c2d6c3911e3d81fd0cd02d89668
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-library-cache"></a>Cache di libreria di cursori
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 Per ogni riga di dati nel set di risultati, la libreria di cursori memorizza nella cache i dati per ogni colonna associata, la lunghezza dei dati in ogni colonna associata e lo stato della riga. La libreria di cursori utilizza i valori della cache restituita attraverso **SQLFetch** e **SQLFetchScroll** e per creare istruzioni di ricerca per operazioni posizionate. Per ulteriori informazioni, vedere [la costruzione di istruzioni di ricerca](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Dati della colonna](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Lunghezza dei dati di colonna](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [Stato di riga](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Percorso della Cache](../../../odbc/reference/appendixes/location-of-cache.md)

