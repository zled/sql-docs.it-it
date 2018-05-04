---
title: 'C a SQL: tempo | Documenti Microsoft'
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
- data conversions from C to SQL types [ODBC], time
- time data type [ODBC]
- converting data from c to SQL types [ODBC], time
ms.assetid: a8da43c9-d9a5-45e5-bd9a-1dd633db2ee0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac288b1b1985d106e88254a23eed2d973425c6f0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
