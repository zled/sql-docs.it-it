---
title: Allocato in modo esplicito i descrittori | Documenti Microsoft
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
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a2e3c3f2941597ed0b4ffedeccc060690110d1c3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="explicitly-allocated-descriptors"></a>Descrittori allocati in modo esplicito
Un'applicazione può allocare in modo esplicito un descrittore di applicazione su una connessione in qualsiasi momento in cui che è connesso al database. Specificando l'handle di descrittore come gestire l'attributo di un'istruzione utilizzando **SQLSetStmtAttr**, l'applicazione indica al driver di utilizzare tale descrittore al posto della corrispondente allocata in modo implicito l'applicazione descrittori. L'applicazione non è possibile specificare i descrittori di implementazione alternativa.  
  
 Un'applicazione è possibile associare più di un'istruzione di un descrittore allocato in modo esplicito. Solo quando un'applicazione è connessa al database di un descrittore può essere un descrittore allocato in modo esplicito. L'applicazione può liberare un descrittore di questo tipo in modo esplicito o implicito liberando la connessione.
