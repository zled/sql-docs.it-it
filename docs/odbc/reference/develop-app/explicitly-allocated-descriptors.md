---
title: Allocato in modo esplicito i descrittori | Documenti Microsoft
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
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7a4679fa6c6d2185f6e474407882080fea6b7c8a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="explicitly-allocated-descriptors"></a>Descrittori allocati in modo esplicito
Un'applicazione può allocare in modo esplicito un descrittore di applicazione su una connessione in qualsiasi momento in cui che è connesso al database. Specificando l'handle di descrittore come gestire l'attributo di un'istruzione utilizzando **SQLSetStmtAttr**, l'applicazione indica al driver di utilizzare tale descrittore al posto della corrispondente allocata in modo implicito l'applicazione descrittori. L'applicazione non è possibile specificare i descrittori di implementazione alternativa.  
  
 Un'applicazione è possibile associare più di un'istruzione di un descrittore allocato in modo esplicito. Solo quando un'applicazione è connessa al database di un descrittore può essere un descrittore allocato in modo esplicito. L'applicazione può liberare un descrittore di questo tipo in modo esplicito o implicito liberando la connessione.
