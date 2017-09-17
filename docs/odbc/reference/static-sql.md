---
title: SQL statico | Documenti Microsoft
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
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1675f70b67f5c600aada546f8caf8eb8b99df99a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="static-sql"></a>SQL statico
Embedded SQL nel [Embedded SQL esempio](../../odbc/reference/embedded-sql-example.md) è noto come SQL statico. SQL statico viene chiamato perché le istruzioni SQL nel programma sono statiche. vale a dire non cambiano ogni volta che viene eseguito il programma. Come descritto nella sezione precedente, queste istruzioni vengono compilate quando viene compilato il resto del programma.  
  
 SQL statico funziona bene in molte situazioni e può essere utilizzato in qualsiasi applicazione per cui l'accesso ai dati può essere determinato in fase di progettazione di programma. Ad esempio, un programma di registrazione ordine utilizza sempre la stessa istruzione per inserire un nuovo ordine e un sistema di prenotazione airline utilizza sempre la stessa istruzione per modificare lo stato di una postazione da disponibile a sono riservati. Ognuna di queste istruzioni potrebbe essere generalizzato tramite l'utilizzo di variabili host. valori diversi possono essere inseriti in un ordine di vendita e che è possibile riservare posti diversi. Poiché tali istruzioni possono essere hardcoded nel programma, tali programmi hanno il vantaggio che le istruzioni devono essere analizzato, convalidato e ottimizzata una sola volta, in fase di compilazione. Questo codice relativamente veloce.
