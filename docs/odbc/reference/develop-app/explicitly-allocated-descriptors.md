---
title: Allocato in modo esplicito i descrittori | Documenti Microsoft
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
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1f09c3d7817fdb3d7f992255a7c2242c515e9748
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="explicitly-allocated-descriptors"></a>Descrittori allocati in modo esplicito
Un'applicazione può allocare in modo esplicito un descrittore di applicazione su una connessione in qualsiasi momento in cui che è connesso al database. Specificando l'handle di descrittore come gestire l'attributo di un'istruzione utilizzando **SQLSetStmtAttr**, l'applicazione indica al driver di utilizzare tale descrittore al posto della corrispondente allocata in modo implicito l'applicazione descrittori. L'applicazione non è possibile specificare i descrittori di implementazione alternativa.  
  
 Un'applicazione è possibile associare più di un'istruzione di un descrittore allocato in modo esplicito. Solo quando un'applicazione è connessa al database di un descrittore può essere un descrittore allocato in modo esplicito. L'applicazione può liberare un descrittore di questo tipo in modo esplicito o implicito liberando la connessione.
