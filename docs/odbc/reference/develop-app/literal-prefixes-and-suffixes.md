---
title: Valore letterale prefissi e suffissi | Documenti Microsoft
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
- interoperability of SQL statements [ODBC], literal prefixes and suffixes
- literals [ODBC], prefixes and suffixes
ms.assetid: 29f468f2-f557-4a92-b31d-569c63cc6272
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f702ed5210b5735a0d3dac418f8296ce274a729b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="literal-prefixes-and-suffixes"></a>Valore letterale prefissi e suffissi
In un'istruzione SQL, un *letterale* è una rappresentazione dei caratteri di un valore effettivo dei dati. Nell'istruzione seguente, ad esempio, ABC, FFFF e 10 sono valori letterali:  
  
```  
SELECT CharCol, BinaryCol, IntegerCol FROM MyTable  
   WHERE CharCol = 'ABC' AND BinaryCol = 0xFFFF AND IntegerCol = 10  
```  
  
 Valori letterali per alcuni tipi di dati richiedono speciali prefissi e suffissi. Nell'esempio precedente, il valore letterale carattere (ABC) richiede una virgoletta singola (') come un prefisso e un suffisso, il valore letterale binario (FFFF) richiede i caratteri 0x come prefisso e il valore letterale integer (10) non richiede un prefisso o suffisso.  
  
 Per tutti i tipi di dati, ad eccezione di date, time e timestamp, le applicazioni interoperabili devono utilizzare i valori restituiti nelle colonne del set di risultati creati:: SQLGetTypeInfo e SQL_VARCHAR **SQLGetTypeInfo**. Per date, time, timestamp e valori letterali intervallo datetime, le applicazioni interoperabili devono utilizzare le sequenze di escape descritte nella sezione precedente.
