---
title: 'Jet: Date, Time e Timestamp letterali | Documenti Microsoft'
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
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc36c46885a358e1ca453901fd72362ed1dbb32b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: Date, Time e Timestamp letterali
Per garantire la massima interoperabilità, le applicazioni devono passare valori letterali di data nel formato canonico ODBC utilizzando la sintassi della clausola di escape:  
  
-   Per i valori letterali data, {d '*valore*'}, dove *valore*e è nel formato "aaaa-mm-gg"  
  
-   Per i valori letterali ora, {t '*valore*'}, dove *valore*e è nel formato "hh"  
  
 Per i valori letterali timestamp {ts'*valore*'}, dove *valore*e è nel formato "aaaa-mm-gg hh: mm: [. f....]".
