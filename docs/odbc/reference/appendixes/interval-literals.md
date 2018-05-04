---
title: Valori letterali di intervallo | Documenti Microsoft
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
- data types [ODBC], interval data types
- interval literals [ODBC]
- interval data type [ODBC], literals
ms.assetid: f9e6c3c7-4f98-483f-89d8-ebc5680f021b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 976a56ea43eb5cb0f6161cc4c3cd4b7e735061ea
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="interval-literals"></a>Valori letterali di intervallo
ODBC richiede che tutti i driver supportano la conversione del tipo di dati SQL_CHAR o SQL_VARCHAR a tutti i tipi di dati di intervallo C. Se l'origine dati sottostante non supporta i tipi di dati di intervallo, tuttavia, il driver deve conoscere il formato corretto del valore nel campo SQL_CHAR per supportare queste conversioni. Analogamente, ODBC richiede che deve disporre di qualsiasi tipo essere convertibile in SQL_CHAR o SQL_VARCHAR, pertanto è necessario sapere quale formato di un intervallo archiviato nel campo carattere un driver di ODBC C. In questa sezione viene descritta la sintassi di valori letterali di intervallo, che scrive il driver deve utilizzare per convalidare i campi SQL_CHAR durante la conversione da o verso tipi di dati di intervallo C.  
  
> [!NOTE]  
>  La sintassi BNF completa per i valori letterali intervallo viene visualizzata nella sezione [sintassi del valore letterale intervallo](../../../odbc/reference/appendixes/interval-literal-syntax.md) nella grammatica SQL di appendice c:.  
  
 Per passare valori letterali di intervallo come parte di un'istruzione SQL, una sintassi della clausola escape è definita per i valori letterali di intervallo. Per ulteriori informazioni, vedere [Date, Time e Timestamp letterali](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Un intervallo di valore letterale è nel formato:  
  
```  
INTERVAL[<sign>] 'value' <interval qualifier>  
```  
  
 dove "Intervallo" indica che il valore letterale carattere è un intervallo. Può essere il segno più o meno; è di fuori della stringa di intervallo ed è facoltativo.  
  
 Il qualificatore di intervallo può essere un campo datetime singolo o essere costituita da due campi di data/ora, nel formato: \< *campo iniziale*> a \< *campo finale*>.  
  
-   Quando l'intervallo è costituita da un singolo campo, l'unico campo può essere un campo non secondo che può essere accompagnato da un valore di precisione iniziale facoltativo racchiuso tra parentesi. Il campo datetime singolo può essere anche un secondo campo che può essere accompagnato dalla precisione iniziale facoltativa, la precisione in secondi frazionari facoltativo racchiuso tra parentesi o entrambi. Se sono presenti per un campo secondi sia una precisione iniziale e una precisione in secondi frazionari, saranno separati da virgole. Se il campo secondi ha una precisione in secondi frazionari, è necessario che abbia una precisione iniziale.  
  
-   Quando l'intervallo è costituita da campi iniziali e finali, il campo iniziale è un campo non secondo che può essere accompagnato dall'intervallo di precisione di campo di iniziale tra parentesi. Il campo finale può essere un campo non secondo o un secondo campo che può essere accompagnato da un valore di precisione in secondi frazionari intervallo tra parentesi.  
  
 La stringa di intervallo in *valore* è racchiuso tra virgolette singole. Può essere un valore letterale anno-mese o un valore letterale ora giornata. Il formato della stringa in *valore* è determinato dalle regole seguenti:  
  
-   La stringa contiene un valore decimale per ogni campo che è implicita la \< *intervallo* *qualificatore*>.  
  
-   Se la precisione di intervallo sono inclusi i campi di anno e mese, i valori di questi campi sono separati da un segno meno.  
  
-   Se la precisione di intervallo sono inclusi i campi giorno e all'ora, i valori di questi campi sono separati da uno spazio.  
  
-   Se la precisione intervallo include ora il campo e i campi di ordine inferiore (minuto e secondo), i valori di questi campi sono separati dai due punti.  
  
-   Se la precisione intervallo include un secondo campo e la precisione dei secondi espressa o implicita è diverso da zero, il carattere immediatamente prima della prima cifra della parte frazionaria del secondo è un punto.  
  
-   Nessun campo può essere più di due cifre, ad eccezione di:  
  
    -   Il valore del campo iniziale può essere, purché l'intervallo, espressa o implicita, precisione iniziale.  
  
    -   La parte frazionaria del secondo campo può essere, purché la precisione dei secondi espressa o implicita.  
  
    -   I campi finali seguono i normali vincoli del calendario gregoriano. (Vedere [vincoli del calendario gregoriano](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md).)  
  
 Nella tabella seguente sono elencati esempi di come incluse nella clausola di escape ODBC per intervalli di valori letterali di intervallo valido. La sintassi della clausola escape è come segue:  
  
> [!NOTE]  
>  *{INTERVALLO sign intervallo-intervallo-qualificatore della stringa}*  
  
|Valore letterale clausola escape|Intervallo specificato|  
|---------------------------|------------------------|  
|{YEAR(4) INTERVALLO '326'}|Specifica un intervallo di anni 326. L'intervallo di precisione iniziale è 4.|  
|{MONTH(3) INTERVALLO '326'}|Specifica un intervallo di mesi 326. L'intervallo di precisione iniziale è 3.|  
|{DAY(4) INTERVALLO '3261'}|Specifica un intervallo di giorni 3261. L'intervallo di precisione iniziale è 4.|  
|{HOUR(3) INTERVALLO '163'}|Specifica un intervallo di giorni 163. L'intervallo di precisione iniziale è 3.|  
|{MINUTE(3) INTERVALLO '163'}|Specifica un intervallo di minuti 163. L'intervallo di precisione iniziale è 3.|  
|{SECOND(3,2) INTERVALLO '223.16'}|Specifica un intervallo di 223.16 secondi. L'intervallo iniziale è 3, e la precisione dei secondi è 2.|  
|{INTERVALLO ' 163-11' YEAR(3) AL MESE}|Specifica un intervallo di 163 anni e 11 mesi. L'intervallo di precisione iniziale è 3.|  
|{INTERVALLO 163 ' 12' DAY(3) A ORA}|Specifica un intervallo di 163 giorni e 12 ore. L'intervallo di precisione iniziale è 3.|  
|{INTERVALLO ' 163 12:39 ' DAY(3) AL MINUTO}|Specifica un intervallo di 163 giorni, 12 ore e 39 minuti. L'intervallo di precisione iniziale è 3.|  
|{INTERVALLO '163 12:39:59.163' DAY(3) A SECOND(3)}|Specifica un intervallo di 163 giorni, 12 ore, 39 minuti e 59.163 secondi. L'intervallo iniziale è 3, e la precisione dei secondi è 3.|  
|{INTERVALLO '163:39' HOUR(3) AL MINUTO}|Specifica un intervallo di 163 ore e 39 minuti. L'intervallo di precisione iniziale è 3.|  
|{INTERVALLO '163:39:59.163' HOUR(3) A SECOND(4)}|Specifica un intervallo di 163 ore, 39 minuti e 59.163 secondi. L'intervallo iniziale è 3, e la precisione dei secondi è 4.|  
|{INTERVALLO '163:59.163' MINUTE(3) A SECOND(5)}|Specifica un intervallo di 163 minuti e 59.163 secondi. L'intervallo iniziale è 3, e la precisione dei secondi è 5.|  
|{INTERVALLO - SECONDO GIORNO '16 23:39:56.23'}|Specifica un intervallo di meno di 16 giorni, 23 ore, 39 minuti e 56.23 secondi. La precisione iniziale implicita è 2, e la precisione dei secondi implicita è 6.|  
  
 Nella tabella seguente sono elencati esempi di valori letterali di intervallo non valido:  
  
|Valore letterale clausola escape|Motivo perché non valido|  
|---------------------------|------------------------|  
|{HOUR(2) INTERVALLO '163'}|La precisione iniziale intervallo è 2, ma il valore del campo iniziale è 163.|  
|{SECOND(2,2) INTERVALLO '223.16'}<br /><br /> {SECOND(3,1) INTERVALLO '223.16'}|Nel primo esempio, la precisione iniziale è troppo piccola, e nel secondo esempio, la precisione dei secondi è troppo piccola.|  
|{INTERVALLO '223.16' SECONDO}<br /><br /> {INTERVALLO '223' ANNO}|Poiché la precisione iniziale non è specificata, il valore predefinito 2, che è troppo piccolo per contenere il valore letterale specificato.|  
|{INTERVALLO '22.1234567' SECONDO}|La precisione dei secondi non è specificata, pertanto il valore predefinito è 6. Il valore letterale presenta sette cifre dopo il separatore decimale.|  
|{INTERVALLO ' 163-13. ' YEAR(3) AL MESE}<br /><br /> {INTERVALLO ' 163 DAY(3) A ORA 65'}<br /><br /> {INTERVALLO '163 62:39' DAY(3) AL MINUTO}<br /><br /> {INTERVALLO '163 12:125:59.163' DAY(3) A SECOND(3)}<br /><br /> {INTERVALLO '163:144' HOUR(3) AL MINUTO}<br /><br /> {INTERVALLO '163:567:234.163' HOUR(3) A SECOND(4)}<br /><br /> {INTERVALLO '163:591.163' MINUTE(3) A SECOND(5)}|Il campo finale non segue le regole del calendario gregoriano.|
