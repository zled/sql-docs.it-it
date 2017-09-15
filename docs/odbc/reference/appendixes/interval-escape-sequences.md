---
title: Le sequenze di Escape di intervallo | Documenti Microsoft
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
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8088c0cb3f85b375423f636d2def8c08c04bbe28
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="interval-escape-sequences"></a>Sequenze di Escape di intervallo
ODBC utilizza le sequenze di escape per i valori letterali di intervallo. La sintassi di questa sequenza di escape è come segue:  
  
 {*intervallo-literal*}  
  
 Per informazioni sulla sintassi BNF di *intervallo-literal*, vedere il [sintassi del valore letterale intervallo](../../../odbc/reference/appendixes/interval-literal-syntax.md) sezione più avanti in questa appendice.  
  
 La sequenza di escape letterale intervallo è supportata se i tipi di dati di intervallo supportati dall'origine dati. Un'applicazione deve chiamare **SQLGetTypeInfo** per determinare se sono supportati i tipi di dati.
