---
title: Funzione SQLRemoveDSNFromIni | Documenti Microsoft
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
- SQLRemoveDSNFromIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDSNFromIni
helpviewer_keywords:
- SQLRemoveDSNFromIni function [ODBC]
ms.assetid: bb2e8273-7b61-4113-bfc8-f7ccc607c811
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 83c51c7363cd031aefa60c71270e3fa5e9f779ed
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlremovedsnfromini-function"></a>SQLRemoveDSNFromIni (funzione)
**Conformità**  
 Introdotta: versione ODBC 1.0  
  
 **Riepilogo**  
 **SQLRemoveDSNFromIni** rimuove le informazioni di sistema di un'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszDSN*  
 [Input] Nome dell'origine dati da rimuovere.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se rimuove l'origine dati o l'origine dati non è presente nel file Odbc.ini. Restituisce FALSE se non è possibile rimuovere l'origine dati.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLRemoveDSNFromIni** restituisce FALSE, un oggetto associato * \*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i * \*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_DSN|DSN non valido.|Il *lpszDSN* argomento non valido.|  
|ODBC_ERROR_REQUEST_FAILED|Richiesta non riuscita|Il programma di installazione: Impossibile rimuovere le informazioni DSN dal Registro di sistema.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLRemoveDSNFromIni** rimuove il nome dell'origine dati dalla sezione [origini dati ODBC] le informazioni di sistema. Rimuove inoltre la sezione specifica di origine dati dalle informazioni di sistema.  
  
 Questa funzione deve essere chiamata solo da una libreria di programma di installazione di driver.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un'origine dati|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Aggiunta, modifica o rimozione di un'origine dati|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Rimuovendo l'origine dati predefinito|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Aggiunta di un nome di origine dati per le informazioni di sistema|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|

