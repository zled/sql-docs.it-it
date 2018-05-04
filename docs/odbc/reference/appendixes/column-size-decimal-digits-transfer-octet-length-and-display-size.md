---
title: Dimensioni della colonna, cifre decimali, la lunghezza dell'ottetto trasferimento, visualizzare la dimensione | Documenti Microsoft
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
- data types [ODBC], column size
- transfer octet length of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- decimal digits of data types [ODBC]
- data types [ODBC], decimal digits
- SQL data types [ODBC], column characteristics
- column size of data types [ODBC]
- data types [ODBC], transfer octet length
ms.assetid: 723107a1-be08-4ea3-a8c0-b2c45d38d1aa
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 55cd483f55ec63542a29b2259d606e2b4aa45dad
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="column-size-decimal-digits-transfer-octet-length-and-display-size---odbc"></a>Dimensioni della colonna, cifre decimali, trasferimento ottetto lunghezza e visualizzare dimensioni - ODBC
Tipi di dati sono caratterizzati da loro dimensioni di colonna (o parametro), cifre decimali, lunghezza e dimensioni di visualizzazione. Le funzioni ODBC seguenti restituiscono questi attributi per un parametro in un'istruzione SQL o per un tipo di dati SQL in un'origine dati. Ogni funzione ODBC restituisce un set diverso di questi attributi, come indicato di seguito:  
  
-   **SQLDescribeCol** restituisce cifre decimali e dimensioni delle colonne vengono descritte la colonna.  
  
-   **SQLDescribeParam** restituisce il parametro di cifre decimali e dimensioni dei parametri viene descritto. **SQLBindParameter** imposta il parametro di dimensione e decimali cifre per un parametro in un'istruzione SQL.  
  
-   Le funzioni di catalogo **SQLColumns**, **SQLProcedureColumns**, e **SQLGetTypeInfo** restituisce gli attributi per una colonna in una tabella, set di risultati o un parametro di routine e gli attributi del catalogo dei tipi di dati nell'origine dati. **SQLColumns** restituisce la dimensione della colonna, cifre decimali e lunghezza di una colonna in tabelle specificate (ad esempio la tabella di base, vista o una tabella di sistema). **SQLProcedureColumns** restituisce la dimensione della colonna, cifre decimali e lunghezza di una colonna in una stored procedure. **SQLGetTypeInfo** restituisce la dimensione massima delle colonne e le cifre decimali minime e massime di un tipo di dati SQL in un'origine dati.  
  
 I valori restituiti da queste funzioni per la colonna o parametro di dimensione corrisponde a "precisione" come definita in ODBC 2. *x*. Tuttavia, i valori non corrispondono necessariamente ai valori restituiti in SQL_DESC_PRECISION o qualsiasi altro campo descrittore uno. Lo stesso vale per le cifre decimali, che corrisponde a "scala" come definita in ODBC 2. *x*. Ma non necessariamente corrispondono ai valori restituiti in SQL_DESC_SCALE o qualsiasi altro campo descrittore uno provengono da campi di descrizione diversi a seconda del tipo di dati. Per ulteriori informazioni, vedere [dimensioni della colonna](../../../odbc/reference/appendixes/column-size.md) e [cifre decimali](../../../odbc/reference/appendixes/decimal-digits.md).  
  
 Analogamente, i valori per la lunghezza dell'ottetto trasferimento non provengono da SQL_DESC_LENGTH. Provengono da SQL_DESC_OCTET_LENGTH di un campo di un descrittore per tutti i tipi carattere e binario. È presente alcun campo di descrizione che contiene queste informazioni per altri tipi.  
  
 Il valore di dimensioni di visualizzazione per tutti i tipi di dati corrisponde al valore in un campo singolo descrittore, colonne SQL_DESC_DISPLAY_SIZE.  
  
 I campi di descrizione descrivono le caratteristiche di un set di risultati. I campi di descrizione non contengono i valori validi, sui dati prima dell'esecuzione di istruzione. I valori della colonna dimensioni, cifre decimali e visualizzare dimensioni restituite da **SQLColumns**, **SQLProcedureColumns**, e **SQLGetTypeInfo**, d'altra parte, restituire caratteristiche degli oggetti di database, ad esempio le colonne della tabella e tipi di dati, che esiste nel catalogo dell'origine dati. Analogamente, nel relativo set di risultati, **SQLColAttribute** restituisce le dimensioni della colonna, cifre decimali e trasferimento ottetto lunghezza delle colonne nell'origine dati; tali valori non sono necessariamente lo stesso di quello dei valori di SQL_DESC_PRECISION, SQL _ DESC_SCALE e campi di descrizione SQL_DESC_OCTET_LENGTH.  
  
 Per ulteriori informazioni su questi campi di descrizione, vedere [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Argomenti correlati:  
  
-   [Dimensione colonna](../../../odbc/reference/appendixes/column-size.md)  
-   [Cifre decimali](../../../odbc/reference/appendixes/decimal-digits.md)  
-   [Lunghezza dell'ottetto di trasferimento](../../../odbc/reference/appendixes/transfer-octet-length.md)  
-   [Dimensioni di visualizzazione](../../../odbc/reference/appendixes/display-size.md)
