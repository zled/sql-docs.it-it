---
title: 'C a SQL: Timestamp | Documenti Microsoft'
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
ms.topic: article
helpviewer_keywords:
- data conversions from C to SQL types [ODBC], timestamp
- timestamp data type [ODBC]
- converting data from c to SQL types [ODBC], timestamp
ms.assetid: 0e08bfff-68f9-4648-9558-09b57fea08ad
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: be38d6accb796666a62324e7a6fd5aefcfa0f372
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="c-to-sql-timestamp"></a>C a SQL: Timestamp
L'identificatore per il tipo di dati C ODBC timestamp è:  
  
 SQL_C_TYPE_TIMESTAMP  
  
 Nella tabella seguente viene illustrato SQL ODBC dei tipi di dati a cui possono essere convertiti i dati di tipo C timestamp. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificatore di tipo SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Lunghezza in byte di colonna > = lunghezza in byte di caratteri<br /><br /> 19 < = lunghezza della colonna byte < lunghezza in byte di caratteri<br /><br /> Colonna lunghezza < 19 byte<br /><br /> Valore di dati non è un timestamp valido|n/d<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Lunghezza in caratteri colonna > = lunghezza in caratteri di dati<br /><br /> 19 < = lunghezza della colonna carattere < lunghezza dei dati in caratteri<br /><br /> Colonna carattere a lunghezza < 19<br /><br /> Valore di dati non è un timestamp valido|n/d<br /><br /> 22001<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|I campi ora sono pari a zero<br /><br /> I campi ora sono diversi da zero<br /><br /> Il valore di dati non contiene una data valida|n/d<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIME|I campi di secondi frazionari sono zero [a]<br /><br /> I campi i secondi frazionari sono diversi da zero [a]<br /><br /> Il valore di dati non contiene un'ora valida|n/d<br /><br /> 22008<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|I campi i secondi frazionari non vengono troncati.<br /><br /> I campi i secondi frazionari vengono troncati<br /><br /> Valore di dati non è un timestamp valido|n/d<br /><br /> 22008<br /><br /> 22007|  
  
 [a] data i campi della struttura di timestamp vengono ignorati.  
  
 Per informazioni su quali sono i valori validi in una struttura SQL_C_TIMESTAMP, vedere [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md), più indietro in questa appendice.  
  
 Quando i dati di tipo timestamp C viene convertiti in dati SQL di tipo carattere, i dati di caratteri risultante sono nel "*aaaa*-*mm*-*gg* *hh*:*mm*:*ss*[.*f...*] "formato.  
  
 Il driver ignora il valore di lunghezza/indicatore quando la conversione dei dati dal tipo di dati timestamp C e si presuppone che le dimensioni del buffer di dati sono la dimensione del tipo di dati timestamp C. Viene passato il valore di lunghezza/indicatore di *StrLen_or_Ind* argomento **SQLPutData** e nel buffer specificato con il *StrLen_or_IndPtr* argomento **SQLBindParameter**. Il buffer dei dati è specificato con il *DataPtr* argomento in **SQLPutData** e *ParameterValuePtr* argomento **SQLBindParameter**.
