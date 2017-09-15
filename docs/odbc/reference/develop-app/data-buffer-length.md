---
title: Lunghezza del Buffer di dati | Documenti Microsoft
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
- data buffers [ODBC], length
- buffers [ODBC], data
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 7288d143-f9e5-4f90-9b31-2549df79c109
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 84bacf4e45760b14515d44a9d81f46de4485ee5f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="data-buffer-length"></a>Lunghezza del Buffer di dati
L'applicazione passa la lunghezza in byte del buffer di dati per il driver in un argomento, denominato *BufferLength* o un nome simile. Ad esempio, nella chiamata seguente a **SQLBindCol**, l'applicazione specifica la lunghezza del *ValuePtr* buffer (**sizeof (***ValuePtr***)**):  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 Un driver restituirà sempre il numero di byte e non il numero di caratteri nell'argomento di lunghezza del buffer di qualsiasi funzione che dispone di un argomento di stringa di output.  
  
 Lunghezza dei buffer di dati è necessari solo per i buffer di output. il driver li utilizza per evitare di scrivere oltre la fine del buffer. Tuttavia, il driver verificherà la lunghezza del buffer di dati solo quando il buffer contiene dati a lunghezza variabile, ad esempio carattere o dati binari. Se il buffer contiene dati a lunghezza fissa, ad esempio una struttura di tipo integer o data, il driver ignora la lunghezza del buffer di dati e si presuppone che il buffer è sufficientemente grande da contenere i dati. viene troncata, mai dati a lunghezza fissa. È pertanto importante per l'applicazione allocare un buffer sufficiente per i dati a lunghezza fissa.  
  
 Si verifica di un troncamento dei dati non output stringhe (ad esempio il nome del cursore restituito per **SQLGetCursorName**), la lunghezza restituita nell'argomento di lunghezza di buffer è la lunghezza massima possibile.  
  
 Lunghezza dei buffer di dati non è necessari per i buffer di input perché il driver non scrivere tali buffer.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Utilizzando i valori di lunghezza/indicatore](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)  
  
-   [Lunghezza dei dati, lunghezza del Buffer e il troncamento](../../../odbc/reference/develop-app/data-length-buffer-length-and-truncation.md)  
  
-   [Dati di tipo carattere e le stringhe C](../../../odbc/reference/develop-app/character-data-and-c-strings.md)
