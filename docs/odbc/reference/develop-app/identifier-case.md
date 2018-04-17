---
title: Identificatore Case | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 122f4dfdfab25f246858b36f7753413d25f2eea4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="identifier-case"></a>Identificatore Case
In istruzioni SQL e gli argomenti di funzione di catalogo, identificatori e gli identificatori tra virgolette possono essere distinzione maiuscole/minuscole o non, che un'applicazione può determinare chiamando **SQLGetInfo** e SQL_IDENTIFIER_CASE SQL_QUOTED_ Opzioni IDENTIFIER_CASE.  
  
 Ognuna di queste opzioni con quattro valori restituiti possibili: uno che informa che l'identificatore o identificatore delimitato case è sensibile e tre che informa che non è sensibile. I tre valori che non fanno distinzione tra maiuscole e descrivono ulteriormente il caso in cui gli identificatori vengono archiviati nel catalogo di sistema. Come gli identificatori vengono archiviati nel catalogo di sistema sono rilevanti solo per scopi di visualizzazione, ad esempio quando un'applicazione consente di visualizzare i risultati di una funzione di catalogo. viene modificata la distinzione maiuscole/minuscole degli identificatori.
