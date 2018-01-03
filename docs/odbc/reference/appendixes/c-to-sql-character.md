---
title: 'C a SQL: carattere | Documenti Microsoft'
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- character data type [ODBC]
- data conversions from C to SQL types [ODBC], character
- converting data from c to SQL types [ODBC], character
ms.assetid: be66188a-ebdb-4c9e-af72-c379886766fa
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1496d6d5a6f130b7eea47ad11a47e763a7958e08
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="c-to-sql-character"></a>C a SQL: carattere
Gli identificatori per il carattere di tipo di dati ODBC C sono:  
  
 SQL_C_CHAR  
  
 SQL_C_WCHAR  
  
 Nella tabella seguente viene illustrato SQL ODBC dei tipi di dati a cui possono essere convertiti i dati di tipo carattere C. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
> [!NOTE]  
>  Quando i dati di caratteri C vengono convertiti in dati Unicode SQL, la lunghezza dei dati Unicode deve essere un numero pari.  
  
|Identificatore di tipo SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Lunghezza in byte dei dati < = lunghezza della colonna.<br /><br /> Lunghezza in byte dei dati > lunghezza della colonna.|n/d<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Lunghezza dei dati di carattere < = lunghezza della colonna.<br /><br /> Lunghezza dei dati in caratteri > lunghezza della colonna.|n/d<br /><br /> 22001|  
|SQL_DECIMAL<br /><br /> SQL_NUMERIC<br /><br /> SQL_TINYINT<br /><br /> SQL_SMALLINT<br /><br /> SQL_INTEGER SQL_BIGINT|Dati convertiti senza troncamento<br /><br /> Convertire dati con il troncamento delle cifre frazionarie [e]<br /><br /> La conversione dei dati comporta la perdita di cifre intero (in contrapposizione frazionari) [e]<br /><br /> Il valore di dati non è un *valore letterale numerico*|n/d<br /><br /> 22001<br /><br /> 22001<br /><br /> 22018|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Dati sono compreso nell'intervallo del tipo di dati a cui il numero viene convertito<br /><br /> Dati non rientra nell'intervallo del tipo di dati a cui il numero viene convertito<br /><br /> Il valore di dati non è un *valore letterale numerico*|n/d<br /><br /> 22003<br /><br /> 22018|  
|SQL_BIT|I dati sono 0 o 1<br /><br /> Dati sono maggiori di 0, minore di 2 e non è uguale a 1<br /><br /> Dati sono minore di 0 o maggiore di o uguale a 2<br /><br /> Dati non sono un *valore letterale numerico*|n/d<br /><br /> 22001<br /><br /> 22003<br /><br /> 22018|  
|SQL_BINARY<br /><br /> SQL_VARBINARY<br /><br /> SQL_LONGVARBINARY|(Lunghezza in byte dei dati) / 2 < = lunghezza di colonna in byte<br /><br /> (Lunghezza in byte dei dati) / 2 > lunghezza di colonna in byte<br /><br /> Valore di dati non è un valore esadecimale|n/d<br /><br /> 22001<br /><br /> 22018|  
|SQL_TYPE_DATE|Valore di dati è un valore valido *valore letterale di data ODBC*<br /><br /> Valore di dati è un valore valido *ODBC-timestamp-literal*; la parte dell'ora è uguale a zero<br /><br /> Valore di dati è un valore valido *ODBC-timestamp-literal*; la parte dell'ora è diverso da zero [a]<br /><br /> Valore di dati non è un valido *valore letterale di data ODBC* o *valore letterale di timestamp ODBC*|n/d<br /><br /> n/d<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIME|Valore di dati è un valore valido *valore letterale di ora ODBC*<br /><br /> Valore di dati è un valore valido *ODBC-timestamp-literal*; frazionari parte relativa ai secondi è pari a zero [b]<br /><br /> Valore di dati è un valore valido *ODBC-timestamp-literal*; frazionari parte relativa ai secondi è diverso da zero [b]<br /><br /> Valore di dati non è un valido *valore letterale di ora ODBC* o *valore letterale di timestamp ODBC*|n/d<br /><br /> n/d<br /><br /> 22008<br /><br /> 22018|  
|SQL_TYPE_TIMESTAMP|Valore di dati è un valore valido *ODBC-timestamp-literal*; frazionari parte relativa ai secondi non troncato<br /><br /> Valore di dati è un valore valido *ODBC-timestamp-literal*; frazionari parte relativa ai secondi troncato<br /><br /> Valore di dati è un valore valido *valore letterale di data ODBC*[c]<br /><br /> Valore di dati è un valore valido *valore letterale di ora ODBC*[d]<br /><br /> Valore di dati non è un valido *valore letterale di data ODBC*, *valore letterale di ora ODBC*, o *valore letterale di timestamp ODBC*|n/d<br /><br /> 22008<br /><br /> n/d<br /><br /> n/d<br /><br /> 22018|  
|Tutti i tipi di intervallo SQL|Valore di dati è un valore valido *il valore dell'intervallo*; nessun troncamento si verifica<br /><br /> Valore di dati è un valore valido *il valore dell'intervallo*; viene troncato il valore in uno dei campi<br /><br /> Il valore di dati non è un intervallo valido di valore letterale|n/d<br /><br /> 22015<br /><br /> 22018|  
  
 [a] la porzione dell'ora del timestamp viene troncata.  
  
 [b] la parte relativa alla data del timestamp viene ignorata.  
  
 [c] la porzione dell'ora del timestamp è impostata su zero.  
  
 [d] la parte relativa alla data del timestamp è impostata sulla data corrente.  
  
 [e] l'origine dati/driver in modo efficace attende fino a quando non è stata ricevuta l'intera stringa (anche se i dati di carattere vengono inviati in parti dalle chiamate a **SQLPutData**) prima di tentare di eseguire la conversione.  
  
 Quando i dati di tipo carattere C viene convertito in numerico, data, ora o data SQL timestamp, iniziali e gli spazi vuoti finali vengono ignorati.  
  
 Quando i dati di caratteri C vengono convertiti in dati binari di SQL, ogni due byte di dati di tipo carattere vengono convertiti in un singolo byte (8 bit) di dati binari. Ogni due byte di dati di tipo carattere rappresenta un numero in formato esadecimale. Ad esempio, "01" viene convertito in un binario 00000001 e "FF" viene convertito in un binario 11111111.  
  
 Il driver sempre converte coppie di cifre esadecimali a byte singoli e ignora il byte di terminazione null. Per questo motivo, se la lunghezza della stringa di caratteri è dispari, l'ultimo byte della stringa (escluso il byte di terminazione null, se presente) non viene convertita.  
  
> [!NOTE]  
>  Gli sviluppatori di applicazioni sono sconsigliati dall'associazione di dati carattere C a un tipo di dati binario SQL. In genere, questa conversione è lenta e poco efficiente.
