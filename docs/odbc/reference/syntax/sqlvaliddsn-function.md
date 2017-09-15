---
title: Funzione SQLValidDSN | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 473670a87ede935267c91537f301589b94666acf
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN (funzione)
**Conformità**  
 Introdotta: versione ODBC 2.0  
  
 **Riepilogo**  
 **SQLValidDSN** controlla la lunghezza e la validità del nome dell'origine dati prima che il nome viene aggiunto per le informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszDSN*  
 [Input] Nome da verificare dell'origine dati.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se il nome dell'origine dati è valido. Restituisce FALSE se il nome dell'origine dati non è valido o la chiamata di funzione non riuscita.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLValidDSN** restituisce FALSE, un oggetto associato * \*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. Oggetto * \*pfErrorCode* se viene restituito solo se la chiamata di funzione ha esito negativo, non ha restituito false perché il nome dell'origine dati non è valido. La tabella seguente elenca i * \*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLValidDSN** viene chiamato da un driver [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) per controllare la lunghezza del nome dell'origine dati e la validità dei singoli caratteri nel nome dell'origine dati. Verifica se la lunghezza del nome è maggiore di SQL_MAX_DSN_LENGTH, come definito in Sqlext. h. (Anche viene verificata la lunghezza del nome dell'origine dati da [SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md).) **SQLValidDSN** controlla se uno qualsiasi dei seguenti caratteri non validi vengono inclusi nel nome dell'origine dati:  
  
 [ ] { } ( ) , ; ? * = ! @ \  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un'origine dati|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (in DLL di installazione)|  
|Aggiunta, modifica o rimozione di un'origine dati|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Scrittura di un nome origine dati per le informazioni di sistema|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
