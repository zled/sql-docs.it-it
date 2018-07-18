---
title: 'SQL a c: carattere | Documenti Microsoft'
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
- converting data from SQL to C types [ODBC], character
- character data type [ODBC]
- data conversions from SQL to C types [ODBC], character
ms.assetid: 7fdb7f38-b64d-48f2-bcb4-1ca96b2bbdb6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db139b1307fa1817e0b9ed709be5ee5db2086756
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sql-to-c-character"></a>SQL carattere c:
Gli identificatori per i tipi di dati carattere SQL ODBC sono:  
  
 SQL_CHAR  
  
 SQL_VARCHAR  
  
 SQL_LONGVARCHAR  
  
 SQL_WCHAR  
  
 SQL_WVARCHAR  
  
 SQL_WLONGVARCHAR  
  
 Nella tabella seguente viene illustrato come ODBC C i tipi di dati a cui possono essere convertiti i dati SQL di tipo carattere. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificatore di tipo C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Lunghezza in byte dei dati < *BufferLength*<br /><br /> Lunghezza in byte dei dati > = *BufferLength*|data<br /><br /> Dati troncati|Lunghezza in byte dei dati<br /><br /> Lunghezza in byte dei dati|n/d<br /><br /> 01004|  
|SQL_C_WCHAR|Lunghezza dei dati in caratteri < *BufferLength*<br /><br /> Lunghezza dei dati in caratteri > = *BufferLength*|data<br /><br /> Dati troncati|Lunghezza dei dati in caratteri<br /><br /> Lunghezza dei dati in caratteri|n/d<br /><br /> 01004|  
|SQL_C_STINYINT SQL_C_UTINYINT SQL_C_TINYINT SQL_C_SBIGINT SQL_C_UBIGINT SQL_C_SSHORT SQL_C_USHORT SQL_C_SHORT SQL_C_SLONG SQL_C_ULONG SQL_C_LONG SQL_C_NUMERIC|I dati convertiti senza troncamento [b]<br /><br /> Convertire dati con il troncamento delle cifre frazionarie [a]<br /><br /> La conversione dei dati comporta la perdita di cifre intero (in contrapposizione frazionari) [a]<br /><br /> Dati non sono un *valore letterale numerico*[b].|data<br /><br /> Dati troncati<br /><br /> Non definito<br /><br /> Non definito|Numero di byte del tipo di dati C<br /><br /> Numero di byte del tipo di dati C<br /><br /> Non definito<br /><br /> Non definito|n/d<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_FLOAT SQL_C_DOUBLE|Dati sono compreso nell'intervallo del tipo di dati a cui il numero viene convertito [a]<br /><br /> Dati non rientra nell'intervallo del tipo di dati a cui il numero viene convertito [a]<br /><br /> Dati non sono un *valore letterale numerico*[b].|data<br /><br /> Non definito<br /><br /> Non definito|Dimensioni del tipo di dati C<br /><br /> Non definito<br /><br /> Non definito|n/d<br /><br /> 22003<br /><br /> 22018|  
_C_BIT|I dati sono 0 o 1<br /><br /> Dati sono maggiori di 0, minore di 2 e non è uguale a 1<br /><br /> Dati sono minore di 0 o maggiore di o uguale a 2<br /><br /> Dati non sono un *valore letterale numerico*|data<br /><br /> Dati troncati<br /><br /> Non definito<br /><br /> Non definito|1 [b]<br /><br /> 1 [b]<br /><br /> Non definito<br /><br /> Non definito|n/d<br /><br /> 01S07<br /><br /> 22003<br /><br /> 22018|  
|SQL_C_BINARY|Lunghezza in byte dei dati < = *BufferLength*<br /><br /> Lunghezza in byte dei dati > *BufferLength*|data<br /><br /> Dati troncati|Lunghezza in byte dei dati<br /><br /> Lunghezza dei dati|n/d<br /><br /> 01004|  
|SQL_C_TYPE_DATE|Valore di dati è un valore valido *valore di data*[a]<br /><br /> Valore di dati è un valore valido *valore timestamp*; la parte dell'ora è uguale a zero [a]<br /><br /> Valore di dati è un valore valido *valore timestamp*; la parte dell'ora è diverso da zero [a], [c]<br /><br /> Valore di dati non è un valido *valore di data* o *valore timestamp*[a]|data<br /><br /> data<br /><br /> Dati troncati<br /><br /> Non definito|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> Non definito|n/d<br /><br /> n/d<br /><br /> 01S07<br /><br /> 22018|  
|SQL_C_TYPE_TIME|Valore di dati è un valore valido *valore di ora e i secondi frazionari, il valore è 0*[a]<br /><br /> Valore di dati è un valore valido *valore timestamp o un valore di ora valido*; frazionari parte relativa ai secondi è pari a zero [a], [d]<br /><br /> Valore di dati è un valore valido *valore timestamp*; frazionari parte relativa ai secondi è diverso da zero [a], [d], [e]<br /><br /> Valore di dati non è un valido *valore di ora* o *valore timestamp*[a]|data<br /><br /> data<br /><br /> Dati troncati<br /><br /> Non definito|6 [b]<br /><br /> 6 [b]<br /><br /> 6 [b]<br /><br /> Non definito|n/d<br /><br /> n/d<br /><br /> 01S07<br /><br /> 22018|  
_C_TYPE_TIMESTAMP|Valore di dati è un valore valido *valore timestamp o un valore di ora valido*; frazionari parte relativa ai secondi non troncato [a]<br /><br /> Valore di dati è un valore valido *valore timestamp o un valore di ora valido*; frazionari parte relativa ai secondi troncato [a]<br /><br /> Valore di dati è un valore valido *valore di data*[a]<br /><br /> Valore di dati è un valore valido *valore di ora*[a]<br /><br /> Valore di dati non è un valido *valore di data*, *valore di ora*, o *valore timestamp*[a]|data<br /><br /> Dati troncati<br /><br /> Dati [f]<br /><br /> Dati [c]<br /><br /> Non definito|16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> 16 [b]<br /><br /> Non definito|n/d<br /><br /> 01S07<br /><br /> n/d<br /><br /> n/d<br /><br /> 22018|  
|Tutti i tipi di intervallo C|Valore di dati è un valore valido *il valore dell'intervallo*; nessun troncamento<br /><br /> Valore di dati è un valore valido *il valore dell'intervallo*; troncamento di uno o più campi finali<br /><br /> Dati sono l'intervallo valido. campo significativo precisione iniziale viene perso<br /><br /> Il valore di dati non è un valore di intervallo valido|data<br /><br /> Dati troncati<br /><br /> Non definito<br /><br /> Non definito|Lunghezza in byte dei dati<br /><br /> Lunghezza in byte dei dati<br /><br /> Non definito<br /><br /> Non definito|n/d<br /><br /> 01S07<br /><br /> 22015<br /><br /> 22018|  
  
 [a] il valore di *BufferLength* viene ignorata per la conversione. Il driver presuppone che le dimensioni di **TargetValuePtr* è la dimensione del tipo di dati C.  
  
 [b] è la dimensione del tipo di dati C corrispondente.  
  
 [c] la porzione dell'ora di *valore timestamp* viene troncato.  
  
 [d] la parte relativa alla data del *valore timestamp* viene ignorato.  
  
 [e] la parte frazionaria dei secondi del timestamp viene troncata.  
  
 [f] i campi di tempo della struttura di timestamp vengono impostati su zero.  
  
 [g] i campi data della struttura di timestamp vengono impostati sulla data corrente.  
  
 Quando i dati SQL carattere vengono convertiti in numerico, data, ora, timestamp o dati di intervallo C, spazi iniziali e finali vengono ignorati.
