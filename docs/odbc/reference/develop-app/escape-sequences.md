---
title: Sequenze di escape | Documenti Microsoft
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
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 716c304225e71455a6c492e9824712806f83e3a8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="escape-sequences"></a>Sequenze di escape
ODBC definisce sequenze di escape contenente grammatica standard per le date, time, timestamp e valori letterali intervallo datetime, chiamate di funzione scalare, **come** predicato caratteri di escape, outer join e le chiamate di procedura. Le applicazioni interoperabili devono utilizzare le sequenze di ogni volta che è possibile.  
  
 Per determinare se un driver supporta le sequenze di escape per data, ora, timestamp o valori letterali intervallo datetime, un'applicazione chiama **SQLGetTypeInfo**. Se l'origine dati supporta una data, ora, timestamp o tipo di dati di intervallo datetime, deve supportare anche la sequenza di escape corrispondente. Per determinare se sono supportate altre sequenze di escape, un'applicazione chiama **SQLGetInfo**.  
  
 Per ulteriori informazioni, vedere [sequenze di Escape ODBC](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md), più avanti in questa sezione.
