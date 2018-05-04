---
title: Sequenze di Escape di date, Time e Timestamp | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC]
- escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC]
ms.assetid: 67b7dee0-e5b1-4469-a626-0c7767852b80
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b3e5edf5d233b4a6767eff6590fd2cea9923e640
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="date-time-and-timestamp-escape-sequences"></a>Date, Time e Timestamp sequenze di Escape
ODBC definisce sequenze di escape per date, time e timestamp letterali. La sintassi delle sequenze di escape è come segue:  
  
```  
  
{d 'value'}  
{t 'value'}  
{ts 'value'}  
```  
  
 Nella notazione BNF, la sintassi è:  
  
```  
  
      ODBC-date-time-escape ::=  
     ODBC-date-escape  
     | ODBC-time-escape  
     | ODBC-timestamp-escapeODBC-date-escape ::=  
     ODBC-esc-initiator d 'date-value' ODBC-esc-terminatorODBC-time-escape ::=  
     ODBC-esc-initiator t 'time-value' ODBC-esc-terminatorODBC-timestamp-escape ::=  
     ODBC-esc-initiator ts 'timestamp-value' ODBC-esc-terminatorODBC-esc-initiator ::= {  
ODBC-esc-terminator ::= }  
date-value ::=   
     years-value date-separator months-value date-separator days-valuetime-value ::=   
     hours-value time-separator minutes-value time-separatorseconds-valuetimestamp-value ::= date-value timestamp-separator time-valuedate-separator ::= -  
time-separator ::= :  
timestamp-separator ::=  
     (The blank character)years-value ::= digit digit digit digitmonths-value ::= digit digitdays-value ::= digit digithours-value ::= digit digitminutes-value ::= digit digitseconds-value ::= digit digit[.digit...]  
```  
  
## <a name="remarks"></a>Osservazioni  
 Se i tipi di dati date, time e timestamp sono supportati dall'origine dati, sono supportate le sequenze di escape di valore letterale data, ora e timestamp. Un'applicazione deve chiamare **SQLGetTypeInfo** per determinare se sono supportati i tipi di dati.
