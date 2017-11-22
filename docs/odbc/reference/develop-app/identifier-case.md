---
title: Identificatore Case | Documenti Microsoft
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
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 17c1d7658b313860fdc3abfe0c756a38046dbfc4
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="identifier-case"></a>Identificatore Case
In istruzioni SQL e gli argomenti di funzione di catalogo, identificatori e gli identificatori tra virgolette possono essere distinzione maiuscole/minuscole o non, che un'applicazione può determinare chiamando **SQLGetInfo** e SQL_IDENTIFIER_CASE SQL_QUOTED_ Opzioni IDENTIFIER_CASE.  
  
 Ognuna di queste opzioni con quattro valori restituiti possibili: uno che informa che l'identificatore o identificatore delimitato case è sensibile e tre che informa che non è sensibile. I tre valori che non fanno distinzione tra maiuscole e descrivono ulteriormente il caso in cui gli identificatori vengono archiviati nel catalogo di sistema. Come gli identificatori vengono archiviati nel catalogo di sistema sono rilevanti solo per scopi di visualizzazione, ad esempio quando un'applicazione consente di visualizzare i risultati di una funzione di catalogo. viene modificata la distinzione maiuscole/minuscole degli identificatori.
