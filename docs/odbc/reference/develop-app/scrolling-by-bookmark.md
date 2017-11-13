---
title: Scorrimento dal segnalibro | Documenti Microsoft
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
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 25ee104e1f2451c0042d1e7530e1cd9284d5892f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="scrolling-by-bookmark"></a>Lo scorrimento in base al segnalibro
Durante il recupero di righe con **SQLFetchScroll**, un'applicazione può utilizzare un segnalibro come base per la selezione di riga iniziale. Si tratta di una forma di indirizzamento assoluto, in quanto non dipende dalla posizione del cursore corrente. Scorrere fino a una riga con segnalibro, l'applicazione chiama **SQLFetchScroll** con un *FetchOrientation* impostato su sql_fetch_bookmark. Questa operazione utilizza il segnalibro a cui fa riferimento l'attributo di istruzione SQL_ATTR_FETCH_BOOKMARK_PTR. L'operazione restituisce il set di righe che inizia con la riga identificata dal segnalibro. Un'applicazione può specificare un offset per l'operazione di *FetchOffset* argomento della chiamata a **SQLFetchScroll**. Quando viene specificato un offset, la prima riga del set di righe restituito è determinata dall'aggiunta il numero di *FetchOffset* argomento per il numero della riga identificata dal segnalibro. Questo utilizzo del *FetchOffset* argomento non è supportato se utilizzato con ODBC 2. *x* driver; quando un'applicazione chiama **SQLFetchScroll** in un'API ODBC 2. *x* driver con *FetchOrientation* impostato su SQL_FETCH_BOOKMARK, il *FetchOffset* argomento deve essere impostato su 0.

