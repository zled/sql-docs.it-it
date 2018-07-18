---
title: Le regole per le conversioni | Documenti Microsoft
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
- numeric data type [ODBC], literals
- conversions with numeric literals [ODBC]
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: 89f846a3-001d-496a-9843-ac9c38dc1762
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d8020afb215724e05201ac0a2a23ff0f39f1642a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="rules-for-conversions"></a>Regole per le conversioni
Le regole in questa sezione per le conversioni che includono valori letterali numerici. Ai fini di queste regole, vengono definiti i termini seguenti:  
  
-   *Archiviare assegnazione:* durante l'invio di dati in una colonna di tabella in un database. Questo errore si verifica durante le chiamate ad **SQLExecute**, **SQLExecDirect**, e **SQLSetPos**. Durante l'assegnazione di archivio, "target" si riferisce a una colonna di database e "origine" fa riferimento a dati nel buffer dell'applicazione.  
  
-   *Assegnazione di recupero:* durante il recupero dei dati dal database nel buffer dell'applicazione. Questo errore si verifica durante le chiamate ad **SQLFetch**, **SQLGetData**, **SQLFetchScroll**, e **SQLSetPos**. Durante l'assegnazione di recupero, i buffer dell'applicazione si intende "target" e "source" fa riferimento alla colonna del database.  
  
-   *CS:* il valore dell'origine del carattere.  
  
-   *NT:* il valore nella destinazione numerica.  
  
-   *NS:* il valore nell'origine numerico.  
  
-   *CT:* il valore nella destinazione di tipo carattere.  
  
-   La precisione di un valore letterale numerico esatto: il numero di cifre che contiene.  
  
-   La scala di un valore letterale numerico esatto: il numero di cifre a destra del periodo di espressa o implicito.  
  
-   La precisione di un valore letterale numerico approssimativo: la precisione del relativo mantissa.  
  
## <a name="character-source-to-numeric-target"></a>Carattere di origine alla destinazione numerico  
 Di seguito sono le regole per la conversione da un'origine di carattere (CS) in una destinazione numerica (NT):  
  
1.  Sostituire il valore ottenuto rimuovendo gli spazi iniziali o finali in CS CS. Se non è valido. CS *valore letterale numerico*, viene restituito l'errore SQLSTATE 22018 (valore di carattere non valido per la specifica del cast).  
  
2.  Sostituire CS con il valore ottenuto rimuovendo gli zeri iniziali prima del separatore decimale, finali zeri dopo il separatore decimale, o entrambi.  
  
3.  Consente di convertire CS NT. Se la conversione comporta la perdita di cifre significative, viene restituito l'errore SQLSTATE 22003 (valore numerico non compreso nell'intervallo). Se la conversione comporta la perdita di cifre non significative, di errore SQLSTATE 01S07 (troncamento frazionario) viene restituito.  
  
## <a name="numeric-source-to-character-target"></a>Numerici di origine alla destinazione di carattere  
 Di seguito sono le regole per la conversione da un'origine numerica (NS) a una destinazione di tipo carattere (CT):  
  
1.  Consente di avere la lunghezza in caratteri di CT. LT Per l'assegnazione di recupero, LT è uguale alla lunghezza del buffer in caratteri meno il numero di byte in carattere di terminazione null per questo set di caratteri.  
  
2.  Casi:  
  
    -   Se NS è un tipo numerico esatto, quindi consentire YP uguale più breve stringa di caratteri che è conforme alla definizione di *letterale numerico esatto* in modo che la scala di YP è lo stesso come fattore di scala di NS e il valore di YP interpretato è la valore assoluto di NS.  
  
    -   Se un tipo numerico approssimato NS, quindi consentire YP essere una stringa di caratteri come indicato di seguito:  
  
         Caso:  
  
         Se NS è uguale a 0, YP è 0.  
  
         Consente di essere più breve stringa di caratteri che è conforme alla definizione di esatta - YSN*valore letterale numerico* e il cui valore interpretato è il valore assoluto di NS. Se la lunghezza di YSN è minore di (*precisione* + 1) del tipo di dati di NS, quindi consentire YP YSN è uguale.  
  
         In caso contrario, YP è il più breve stringa di caratteri che è conforme alla definizione di *letterale numerici approssimati* il cui valore interpretato è il valore assoluto di NS e il cui *mantissa* è costituito da un singolo *cifra* vale a dire non '0', seguito da un *periodo* e *intero senza segno*.  
  
3.  Caso:  
  
    -   Se NS è minore di 0, quindi consentire Y essere il risultato di:  
  
         '-' &AMP;#124; &AMP;#124; YP  
  
         in '&#124;&#124;' è l'operatore di concatenazione di stringhe.  
  
         In caso contrario, lasciare Y YP è uguale.  
  
4.  Si supponga che applica sia la lunghezza in caratteri di Y.  
  
5.  Caso:  
  
    -   Se ora è uguale a lungo termine, CT è impostato su Y.  
  
    -   Se ora è inferiore a lungo termine, quindi CT impostazione è Y estesi a destra il numero appropriato di spazi.  
  
         In caso contrario (Rispondi > LT), copiarne i primi caratteri LT di Y CT.  
  
         Caso:  
  
         Se si tratta di un'assegnazione di archivio, restituire l'errore SQLSTATE 22001 (dati String, troncati a destra).  
  
         Se si tratta di assegnazione di recupero, restituire il messaggio di avviso SQLSTATE 01004 (dati String, troncati a destra). Quando la copia comporta la perdita di cifre frazionarie (diverso da zero finali), è definito dal driver se si verifica una delle operazioni seguenti:  
  
         (1) il driver tronca la stringa y a una scala appropriata (che può essere anche zero) e scrive il risultato CT.  
  
         (2) il driver viene arrotondata la stringa di Y a una scala appropriata (che può essere anche zero) e scrive il risultato CT.  
  
         (3) il driver non tronca né Arrotonda ma copia solo i primi caratteri LT di Y in CT.
