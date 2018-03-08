---
title: 'SQL in formato binario c: | Documenti Microsoft'
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
- converting data from SQL to c types [ODBC], binary
- binary data type [ODBC]
- data conversions from SQL to C types [ODBC], binary
- binary data transfers [ODBC]
ms.assetid: 8c519072-ae4c-4d32-9d4e-775e3d3d6389
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 293c18d2206d1b034eadc532f8850c6599e904e1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sql-to-c-binary"></a>SQL in formato binario c:
Gli identificatori per i tipi di dati SQL ODBC binari sono:  
  
 SQL_BINARY  
  
 SQL_VARBINARY  
  
 SQL_LONGVARBINARY  
  
 Nella tabella seguente viene illustrato ODBC C a tipi di dati a cui possono essere convertiti i dati binari di SQL. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificatore di tipo C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|(Lunghezza in byte dei dati) \* 2 < *BufferLength*<br /><br /> (Lunghezza in byte dei dati) \* 2 > = *BufferLength*|data<br /><br /> Dati troncati|Lunghezza in byte dei dati<br /><br /> Lunghezza in byte dei dati|n/d<br /><br /> 01004|  
|SQL_C_WCHAR|(Lunghezza in caratteri di dati) \* 2 < *BufferLength*<br /><br /> (Lunghezza in caratteri di dati) \* 2 > = *BufferLength*|data<br /><br /> Dati troncati|Lunghezza dei dati in caratteri<br /><br /> Lunghezza dei dati in caratteri|n/d<br /><br /> 01004|  
|SQL_C_BINARY|Lunghezza in byte dei dati < = *BufferLength*<br /><br /> Lunghezza in byte dei dati > *BufferLength*|data<br /><br /> Dati troncati|Lunghezza in byte dei dati<br /><br /> Lunghezza in byte dei dati|n/d<br /><br /> 01004|  
  
 Quando i dati binari di SQL viene convertiti in dati di tipo carattere C, ogni byte (8 bit) dei dati di origine è rappresentata come due caratteri ASCII. Questi caratteri sono la rappresentazione di caratteri ASCII del numero in formato esadecimale. Ad esempio, un 00000001 binario viene convertito in "01" e un binario 11111111 viene convertito in "FF".  
  
 Il driver sempre converte i byte singoli in coppie di cifre esadecimali e termina la stringa di caratteri con un byte null. Per questo motivo, se *BufferLength* è pari ed è minore della lunghezza dei dati convertiti, l'ultimo byte del **TargetValuePtr* buffer non viene utilizzato. (I dati convertiti richiedono un numero pari di byte, il byte al penultimo è un byte null e non può essere utilizzato l'ultimo byte.)  
  
> [!NOTE]  
>  Gli sviluppatori di applicazioni sono sconsigliati dall'associazione di dati binari SQL a un tipo di dati carattere C. In genere, questa conversione è lenta e poco efficiente.
