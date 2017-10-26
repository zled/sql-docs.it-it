---
title: Indirizzo del Buffer di dati | Documenti Microsoft
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
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7d57b8ec52324dd4bec320b6179507ab3102e629
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="data-buffer-address"></a>Indirizzo del Buffer di dati
L'applicazione passa l'indirizzo del buffer di dati per il driver in un argomento, spesso denominato *ValuePtr* o un nome simile. Ad esempio, nella chiamata seguente a **SQLBindCol**, l'applicazione specifica l'indirizzo del *data* variabile:  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Come accennato nel [allocazione e liberando buffer](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) sezione, l'indirizzo di un buffer posticipato deve rimanere valido fino a quando il buffer non è associato.  
  
 A meno che non è vietato in particolare, l'indirizzo di un buffer di dati può essere un puntatore null. Per i buffer utilizzati per inviare dati al driver, in questo modo il driver ignorare le informazioni contenute in genere nel buffer. Per i buffer utilizzati per recuperare dati dal driver, in questo modo il driver non restituire un valore. In entrambi i casi, il driver ignora l'argomento di lunghezza del buffer di dati corrispondente.

