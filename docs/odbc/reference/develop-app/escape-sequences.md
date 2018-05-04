---
title: Sequenze di escape | Documenti Microsoft
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
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9bb389cba92f45373e7fc693c9c4477d50a702a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="escape-sequences"></a>Sequenze di escape
ODBC definisce sequenze di escape contenente grammatica standard per le date, time, timestamp e valori letterali intervallo datetime, chiamate di funzione scalare, **come** predicato caratteri di escape, outer join e le chiamate di procedura. Le applicazioni interoperabili devono utilizzare le sequenze di ogni volta che è possibile.  
  
 Per determinare se un driver supporta le sequenze di escape per data, ora, timestamp o valori letterali intervallo datetime, un'applicazione chiama **SQLGetTypeInfo**. Se l'origine dati supporta una data, ora, timestamp o tipo di dati di intervallo datetime, deve supportare anche la sequenza di escape corrispondente. Per determinare se sono supportate altre sequenze di escape, un'applicazione chiama **SQLGetInfo**.  
  
 Per ulteriori informazioni, vedere [sequenze di Escape ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md), più avanti in questa sezione.
