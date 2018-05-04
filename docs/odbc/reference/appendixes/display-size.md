---
title: Dimensioni di visualizzazione | Documenti Microsoft
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
- display size of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- SQL data types [ODBC], column characteristics
ms.assetid: 9f7f766f-2492-463c-aab7-f2476e222042
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9a4735e4e05c4ffe3b9f22f94149c027c1da1034
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="display-size"></a>Dimensioni di visualizzazione
Le dimensioni di visualizzazione di una colonna sono il numero massimo di caratteri necessari per visualizzare i dati in formato carattere. Nella tabella seguente definisce le dimensioni di visualizzazione per ogni tipo di dati SQL ODBC.  
  
|Identificatore di tipo SQL|Dimensioni di visualizzazione|  
|-------------------------|------------------|  
|Tutti i tipi di carattere [a]|Il definito (per i tipi) o massimo (per i tipi di variabile) numero di caratteri necessari per visualizzare i dati in formato carattere.|  
|SQL_DECIMAL SQL_NUMERIC|La precisione della colonna più di 2 (un segno, *precisione* cifre e un separatore decimale). Ad esempio, le dimensioni di visualizzazione di una colonna definita come NUMERIC(10,3) sono 12.|  
|SQL_BIT|1 (1 cifra).|  
|SQL_TINYINT|4 se firmato (con un segno e 3 cifre) o 3 se unsigned (3 cifre).|  
|SQL_SMALLINT|6 se firmato (con un segno e 5 cifre) o 5 se unsigned (5 cifre).|  
|SQL_INTEGER|11 se firmato (con un segno e 10 cifre) o 10 se unsigned (10 cifre).|  
|SQL_BIGINT|20 (un segno e 19 se firmato o 20 cifre se unsigned).|  
|SQL_REAL|14 (un segno di 7 cifre, un separatore decimale, la lettera *E*, un segno e 2 cifre).|  
|SQL_FLOAT SQL_DOUBLE|24 (il segno, 15 cifre, un separatore decimale, la lettera *E*, un segno e 3 cifre).|  
|Tutti i tipi binari [a]|Il definito o massimo (per i tipi di variabile) 2 di tempi di lunghezza della colonna. (Ogni byte binario è rappresentato da un numero esadecimale a 2 cifre).|  
|SQL_TYPE_DATE|10 (una data nel formato *aaaa-mm-gg*).|  
|SQL_TYPE_TIME|8 (un'ora nel formato *hh: mm:*)<br /><br /> - oppure -<br /><br /> 9 + *s* (un'ora nel formato *hh: mm:*[. fff...], dove *s* è la precisione dei secondi frazionari).|  
|SQL_TYPE_TIMESTAMP|19 (per un timestamp di *aaaa-mm-gg hh: mm:* formato)<br /><br /> - oppure -<br /><br /> 20 + *s* (per un timestamp nel *aaaa-mm-gg hh: mm:* formato [. fff], dove *s* è la precisione dei secondi frazionari).|  
|Tutti i tipi di dati di intervallo|Vedere [lunghezza del tipo di dati di intervallo](../../../odbc/reference/appendixes/interval-data-type-length.md).|  
|SQL_GUID|36 (il numero di caratteri di *aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee* formato|  
  
 [a] se il driver non è possibile determinare la lunghezza di colonna o parametro dei tipi di variabili, restituirà SQL_NO_TOTAL.
