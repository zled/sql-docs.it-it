---
title: 'C a SQL: tempo | Documenti Microsoft'
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
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6f1a59c15d2ebf1866d4543fa89662888154d4da
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-time"></a>C a SQL: ora
L'identificatore per il tipo di dati ODBC C ora è:  
  
 SQL_C_TYPE_TIME  
  
 Nella tabella seguente viene illustrato SQL ODBC dei tipi di dati a cui possono essere convertiti i dati della fase C. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificatore di tipo SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Lunghezza in byte di colonna > = 8<br /><br /> Colonna lunghezza < 8 byte<br /><br /> Valore di dati non è valida|n/d<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Lunghezza in caratteri colonna > = 8<br /><br /> Colonna carattere a lunghezza < 8<br /><br /> Valore di dati non è valida|n/d<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_TIME|Il valore di dati è un'ora valida<br /><br /> Valore di dati non è valida|n/d<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Il valore di dati è un'ora valida [a]<br /><br /> Valore di dati non è valida|n/d<br /><br /> 22007|  
  
 [La data di parte del timestamp viene impostata sulla data corrente e i secondi frazionari parte del timestamp è impostata su zero, a].  
  
 Per informazioni su quali sono i valori validi in una struttura SQL_C_TYPE_TIME, vedere [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md), più indietro in questa appendice.  
  
 Quando i dati della fase C viene convertiti in dati SQL di tipo carattere, i dati di caratteri risultante sono nel "*hh*:*mm*:*ss*" formato.  
  
 Il driver ignora il valore di lunghezza/indicatore durante la conversione dei dati dal momento in cui tipo di dati C e si presuppone che le dimensioni del buffer di dati sono la dimensione del tipo di dati C di tempo. Viene passato il valore di lunghezza/indicatore di *StrLen_or_Ind* argomento **SQLPutData** e nel buffer specificato con il *StrLen_or_IndPtr* argomento **SQLBindParameter**. Il buffer dei dati è specificato con il *DataPtr* argomento in **SQLPutData** e *ParameterValuePtr* argomento **SQLBindParameter**.
