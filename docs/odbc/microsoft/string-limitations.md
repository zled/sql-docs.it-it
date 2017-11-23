---
title: Stringa limitazioni | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 260a530210b2e336067f2036f632cf347c1654f9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="string-limitations"></a>Limitazioni di stringa
La lunghezza massima di una stringa di istruzione SQL è 65.000 caratteri.  
  
 Quando viene utilizzato il driver Microsoft Access, SQL-92 solo le costanti stringa (tra virgolette singole, virgolette doppie non) sono supportate.  
  
 Il carattere barra verticale (&#124;) non può essere utilizzato in una stringa, se il carattere è racchiuso tra virgolette indietro o non.  
  
 Per garantire la massima interoperabilità, le applicazioni devono passare stringhe nei parametri, anziché il passaggio tra virgolette stringhe.
