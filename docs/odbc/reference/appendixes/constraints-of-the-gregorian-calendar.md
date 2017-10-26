---
title: I vincoli del calendario gregoriano | Documenti Microsoft
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
- data types [ODBC], Gregorian calendar
- Gregorian calendar [ODBC]
ms.assetid: 70667410-c582-4369-8e06-9d98e21cd2bf
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1b149b1e9df8338b5502d57e6e7eb355b66bcc3f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="constraints-of-the-gregorian-calendar"></a>Vincoli del calendario gregoriano
Tipi di dati date e datetime e i campi dei tipi di dati di intervallo finali devono essere conforme ai vincoli del calendario gregoriano. Questi vincoli sono i seguenti:  
  
-   Il valore del campo mese deve essere compreso tra 1 e 12 inclusi.  
  
-   Il valore del campo giorno deve essere compreso nell'intervallo compreso tra 1 e il numero di giorni del mese. Il numero di giorni del mese è determinato dai valori dei campi anni e mesi e può essere 28, 29, 30 o 31. (Il numero di giorni del mese può inoltre dipendere si tratti di un anno bisestile.)  
  
-   Il valore del campo ora deve essere compreso tra 0 e 23, inclusi.  
  
-   Il valore del campo relativo ai minuti deve essere compreso tra 0 e 59.  
  
-   Per il campo secondi finali dei tipi di dati di intervallo, il valore del campo secondi deve essere compreso tra 0 e 59,9 (*n*), inclusi, in cui * n * è il numero di cifre di precisione frazionaria dei secondi.  
  
-   Per il campo secondi finali dei tipi di dati datetime, il valore del campo secondi deve essere compreso tra 0 e 61.9 (*n*), inclusi, in cui * n * specifica il numero di "9" cifre e il valore di * n * è la precisione dei secondi frazionari. (L'intervallo di secondi consente un massimo di due secondi di compensazione gestire la sincronizzazione dell'ora siderale).

