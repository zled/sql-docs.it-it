---
title: Scorrimento dal segnalibro | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
- scrolling rows [ODBC]
ms.assetid: 4862f098-41a4-4bd2-894e-f71bb97f9bc0
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 823929a98b3fc7b016f8bc1dc3fa1c2ed982b9c0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="scrolling-by-bookmark"></a>Lo scorrimento in base al segnalibro
Durante il recupero di righe con **SQLFetchScroll**, un'applicazione può utilizzare un segnalibro come base per la selezione di riga iniziale. Si tratta di una forma di indirizzamento assoluto, in quanto non dipende dalla posizione del cursore corrente. Scorrere fino a una riga con segnalibro, l'applicazione chiama **SQLFetchScroll** con un *FetchOrientation* impostato su sql_fetch_bookmark. Questa operazione utilizza il segnalibro a cui fa riferimento l'attributo di istruzione SQL_ATTR_FETCH_BOOKMARK_PTR. L'operazione restituisce il set di righe che inizia con la riga identificata dal segnalibro. Un'applicazione può specificare un offset per l'operazione di *FetchOffset* argomento della chiamata a **SQLFetchScroll**. Quando viene specificato un offset, la prima riga del set di righe restituito è determinata dall'aggiunta il numero di *FetchOffset* argomento per il numero della riga identificata dal segnalibro. Questo utilizzo del *FetchOffset* argomento non è supportato se utilizzato con ODBC 2. *x* driver; quando un'applicazione chiama **SQLFetchScroll** in un'API ODBC 2. *x* driver con *FetchOrientation* impostato su SQL_FETCH_BOOKMARK, il *FetchOffset* argomento deve essere impostato su 0.
