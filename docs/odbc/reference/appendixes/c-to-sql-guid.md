---
title: 'C a SQL: GUID | Documenti Microsoft'
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
- converting data from c to SQL types [ODBC], guid
- data conversions from C to SQL types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: 9168b0b6-a828-4fef-b8cd-bdf439776f23
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 36aadcf415fcf447f87f5952f6b6d32c921b07c2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="c-to-sql-guid"></a>C a SQL: GUID
L'identificatore per il tipo di dati C ODBC GUID è:  
  
 SQL_C_GUID  
  
 Nella tabella seguente viene illustrato SQL ODBC dei tipi di dati a cui possono essere convertiti i dati di GUID C. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificatore di tipo SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR|Lunghezza in byte di colonna > = 36|n/d|  
|SQL_VARCHAR|Colonna lunghezza < 36 byte|22001|  
|SQL_LONGVARCHAR|Valore di dati non è un GUID valido|22018|  
|SQL_WCHAR|Lunghezza in caratteri colonna > = 36|n/d|  
|SQL_WVARCHAR|Colonna carattere a lunghezza < 36|22001|  
|SQL_WLONGVARCHAR|Valore di dati non è un GUID valido|22018|  
|SQL_GUID|Nessuno, [a]|n/d|  
  
 [a] tutti i valori esadecimali sono validi come un GUID.  
  
 Il driver ignora il valore di lunghezza/indicatore quando la conversione dei dati dal tipo di dati GUID C e si presuppone che le dimensioni del buffer di dati sono la dimensione del tipo di dati GUID C. Viene passato il valore di lunghezza/indicatore di *StrLen_or_Ind* argomento **SQLPutData** e nel buffer specificato con il *StrLen_or_IndPtr* argomento **SQLBindParameter**. Il buffer dei dati è specificato con il *DataPtr* argomento in **SQLPutData** e *ParameterValuePtr* argomento **SQLBindParameter**.

