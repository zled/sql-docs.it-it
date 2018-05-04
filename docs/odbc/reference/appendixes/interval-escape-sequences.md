---
title: Le sequenze di Escape di intervallo | Documenti Microsoft
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
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e3a475170fed349a5bf85eb4f23bb93fe4ae804
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="interval-escape-sequences"></a>Sequenze di Escape di intervallo
ODBC utilizza le sequenze di escape per i valori letterali di intervallo. La sintassi di questa sequenza di escape è come segue:  
  
 {*intervallo-literal*}  
  
 Per informazioni sulla sintassi BNF di *intervallo-literal*, vedere il [sintassi del valore letterale intervallo](../../../odbc/reference/appendixes/interval-literal-syntax.md) sezione più avanti in questa appendice.  
  
 La sequenza di escape letterale intervallo è supportata se i tipi di dati di intervallo supportati dall'origine dati. Un'applicazione deve chiamare **SQLGetTypeInfo** per determinare se sono supportati i tipi di dati.
