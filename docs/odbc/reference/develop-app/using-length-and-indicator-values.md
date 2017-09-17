---
title: Utilizzando i valori di lunghezza e indicatore | Documenti Microsoft
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
- length/indicator buffers [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 849792f1-cb1e-4bc2-b568-c0aff0b66199
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f615aa92da79c391e84539fdf5cf402d523ab690
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-length-and-indicator-values"></a>Utilizzo di lunghezza e i valori di indicatore
Il buffer di lunghezza/indicatore viene utilizzato per passare la lunghezza in byte dei dati nel buffer di dati o un indicatore speciale, ad esempio SQL_NULL_DATA, che indica che i dati sono NULL. A seconda della funzione in cui viene utilizzato, un buffer di lunghezza/indicatore è definito come un SQLINTEGER o un SQLSMALLINT. Pertanto, un solo argomento, è necessario per una descrizione. Se il buffer di dati è un buffer di input nondeferred, questo argomento contiene la lunghezza in byte dei dati stessi o un valore dell'indicatore. È spesso denominato *StrLen_or_Ind* o un nome simile. Ad esempio, il codice seguente chiama **SQLPutData** per passare un buffer completo dei dati; la lunghezza in byte (*ValueLen*) viene passato direttamente perché il buffer dei dati (*ValuePtr*) è un buffer di input.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLen;  
  
// Call local function to place data in ValuePtr. In ValueLen, return the  
// number of bytes of data placed in ValuePtr. If there is not enough  
// data, this will be less than 50.  
FillBuffer(ValuePtr, sizeof(ValuePtr), &ValueLen);  
  
// Call SQLPutData to send the data to the driver.  
SQLPutData(hstmt, ValuePtr, ValueLen);  
```  
  
 Se il buffer di dati è un buffer di input posticipato, un buffer di output nondeferred o un buffer di output, l'argomento contiene l'indirizzo del buffer di lunghezza/indicatore. È spesso denominato *StrLen_or_IndPtr* o un nome simile. Ad esempio, il codice seguente chiama **SQLGetData** per recuperare un buffer completo dei dati; la lunghezza in byte viene restituita all'applicazione nel buffer di lunghezza/indicatore (*ValueLenOrInd*), il cui indirizzo è passato a **SQLGetData** perché il buffer di dati corrispondente (*ValuePtr*) è un buffer di output nondeferred.  
  
```  
SQLCHAR      ValuePtr[50];  
SQLINTEGER   ValueLenOrInd;  
SQLGetData(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr), &ValueLenOrInd);  
```  
  
 A meno che non è vietato in particolare, un argomento di buffer di lunghezza/indicatore può essere 0 (se nondeferred input) o un puntatore null (se output o input posticipata). Per i buffer di input, in questo modo il driver ignorare la lunghezza in byte dei dati. Restituisce un errore durante il passaggio di dati a lunghezza variabile, ma è comune quando si passano dati non null, a lunghezza fissa, perché è necessaria una lunghezza né un valore dell'indicatore. Per i buffer di output, in questo modo il driver a non restituire la lunghezza in byte dei dati o un valore dell'indicatore. Si tratta di un errore se i dati restituiti dal driver sono NULL, ma sono comuni quando si recuperano dati a lunghezza fissa e non ammette valori null, perché è necessaria una lunghezza né un valore dell'indicatore.  
  
 Come l'indirizzo di un buffer di dati posticipata quando viene passato al driver, l'indirizzo di un buffer di lunghezza/indicatore posticipata deve rimanere valido fino a quando il buffer non è associato.  
  
 Le lunghezze seguenti sono valide come valori di lunghezza/indicatore:  
  
-   *n*, dove * n * > 0.  
  
-   0.  
  
-   SQL_NTS. Una stringa inviata al driver nel buffer di dati corrispondente è con terminazione null; Questo è un modo pratico per i programmatori di C da passare stringhe senza la necessità di calcolare la lunghezza in byte. Questo valore è valido solo quando l'applicazione invia dati al driver. Quando il driver restituisce i dati per l'applicazione, restituirà sempre la lunghezza di byte effettiva dei dati.  
  
 I valori seguenti sono validi come valori di lunghezza/indicatore. SQL_NULL_DATA viene archiviato nel campo SQL_DESC_INDICATOR_PTR descrittore. tutti gli altri valori vengono archiviati nel campo SQL_DESC_OCTET_LENGTH_PTR descrittore.  
  
-   SQL_NULL_DATA. I dati sono un valore di dati NULL e il valore nel buffer di dati corrispondente viene ignorato. Questo valore è consentito solo per i dati SQL inviati o recuperati dal driver.  
  
-   SQL_DATA_AT_EXEC. Il buffer di dati non contiene alcun dato. Al contrario, i dati verranno inviati con **SQLPutData** quando viene eseguita l'istruzione o **SQLBulkOperations** o **SQLSetPos** viene chiamato. Questo valore è consentito solo per i dati SQL inviati al driver. Per ulteriori informazioni, vedere [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md), [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md), e [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
-   Risultato di SQL_LEN_DATA_AT_EXEC (*lunghezza*) (macro). Questo valore è simile a SQL_DATA_AT_EXEC. Per ulteriori informazioni, vedere [l'invio di dati Long](../../../odbc/reference/develop-app/sending-long-data.md).  
  
-   SQL_NO_TOTAL. Il driver non è possibile determinare il numero di byte di dati long ancora disponibili da restituire in un buffer di output. Questo valore è consentito solo per i dati SQL recuperati dal driver.  
  
-   SQL_DEFAULT_PARAM. Una stored procedure consiste nell'usare il valore predefinito di un parametro di input in una stored procedure anziché il valore nel buffer di dati corrispondente.  
  
-   SQL_COLUMN_IGNORE. **SQLBulkOperations** o **SQLSetPos** consente di ignorare il valore nel buffer di dati. Quando si aggiorna una riga di dati da una chiamata a **SQLBulkOperations** o **SQLSetPos,** non viene modificato il valore della colonna. Quando si inserisce una nuova riga di dati da una chiamata a **SQLBulkOperations**, il valore della colonna è impostato sul valore predefinito o se la colonna non ha un valore predefinito, null.
