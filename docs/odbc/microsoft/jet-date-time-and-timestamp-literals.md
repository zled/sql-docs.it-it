---
title: 'Jet: Date, Time e Timestamp letterali | Documenti Microsoft'
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
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c1a98ca0b68198dada19e4ac81f8637798a99b95
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: Date, Time e Timestamp letterali
Per garantire la massima interoperabilità, le applicazioni devono passare valori letterali di data nel formato canonico ODBC utilizzando la sintassi della clausola di escape:  
  
-   Per i valori letterali data, {d '*valore*'}, dove *valore*e è nel formato "aaaa-mm-gg"  
  
-   Per i valori letterali ora, {t '*valore*'}, dove *valore*e è nel formato "hh"  
  
 Per i valori letterali timestamp {ts'*valore*'}, dove *valore*e è nel formato "aaaa-mm-gg hh: mm: [. f....]".

