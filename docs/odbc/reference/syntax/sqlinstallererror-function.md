---
title: Funzione SQLInstallerError | Documenti Microsoft
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
apiname:
- SQLInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallerError
helpviewer_keywords:
- SQLInstallerError [ODBC]
ms.assetid: e6474b79-4d55-458f-81ce-abfafe357f83
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f2f23e236da96615c08ccf3c2841da650d9d5730
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlinstallererror-function"></a>SQLInstallerError (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLInstallerError** restituisce le informazioni di stato o di errore per le funzioni di programma di installazione ODBC.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Argomenti  
 *su iError*  
 [Input] Numero di record di errore. I numeri validi sono da 1 a 8.  
  
 *pfErrorCode*  
 [Output] Codice di errore di programma di installazione. (Per ulteriori informazioni, vedere "Commenti".)  
  
 *lpszErrorMsg*  
 [Output] Puntatore alla risorsa di archiviazione per il testo del messaggio di errore.  
  
 *cbErrorMsgMax*  
 [Input] Lunghezza massima del *szErrorMsg* buffer. Deve essere minore o uguale a SQL_MAX_MESSAGE_LENGTH meno il carattere di terminazione null.  
  
 *cbErrorMsgMax*  
 [Input] Lunghezza massima del *szErrorMsg* buffer. Deve essere minore o uguale a SQL_MAX_MESSAGE_LENGTH meno il carattere di terminazione null.  
  
 *pcbErrorMsg*  
 [Output] Puntatore al numero totale di byte (escluso il carattere di terminazione null) disponibile per restituire *lpszErrorMsg*. Se il numero di byte disponibili da restituire è maggiore o uguale a *cbErrorMsgMax*, il testo del messaggio di errore in *lpszErrorMsg* viene troncato a *cbErrorMsgMax* meno il byte di caratteri di terminazione null. Il *pcbErrorMsg* argomento può essere un puntatore null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA o SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostica  
 **SQLInstallerError** non registrare i valori di errore per se stesso. **SQLInstallerError** restituisce SQL_NO_DATA quando non è possibile recuperare le informazioni di errore (nel qual caso *pfErrorCode* è definito). Se **SQLInstallerError** non è possibile accedere ai valori di errore per qualsiasi motivo che normalmente restituisce SQL_ERROR, **SQLInstallerError** restituisce SQL_ERROR ma non tutti i valori di errore. Se non si conosce la lunghezza della stringa di avviso (*lpszErrorMsg*), è possibile impostare *lpszErrorMsg* su NULL e chiamare **SQLInstallerError**. **SQLInstallerError** verrà quindi restituito la lunghezza della stringa di avviso in *cbErrorMsgMax*. Se il buffer per il messaggio di errore è troppo breve, **SQLInstallerError** restituisce SQL_SUCCESS_WITH_INFO e corrette *pfErrorCode* valore per **SQLInstallerError**.  
  
 Per determinare se un troncamento si è verificato nel messaggio di errore, un'applicazione è possibile confrontare il valore di *cbErrorMsgMax* argomento per la lunghezza effettiva del testo del messaggio scritto il *pcbErrorMsg* argomento. Se il troncamento, la lunghezza del buffer corrette deve essere allocata per *lpszErrorMsg* e **SQLInstallerError** deve essere chiamato nuovamente con il corrispondente *su iError*record.  
  
## <a name="comments"></a>Commenti  
 Un'applicazione chiama **SQLInstallerError** quando una precedente chiamata alla funzione di programma di installazione ODBC restituisce FALSE. Le funzioni di programma di installazione programma di installazione e driver o funzione di conversione ODBC registra zero o più errori solo quando la funzione ha esito negativo (restituisce FALSE); Pertanto, un'applicazione chiama **SQLInstallerError** solo dopo l'esito negativo di una funzione di programma di installazione ODBC.  
  
 La coda di errore di programma di installazione ODBC viene scaricata ogni volta che viene chiamata una funzione di programma di installazione di nuovo. Pertanto, un'applicazione non è possibile prevedere di recuperare gli errori di funzioni diverso dopo l'ultima chiamata di funzione di programma di installazione.  
  
 Per recuperare gli errori più di una chiamata di funzione, un'applicazione chiama **SQLInstallerError** più volte.  
  
 Quando non sono disponibili informazioni aggiuntive, **SQLInstallerError** restituisce SQL_NO_DATA, il *pfErrorCode* argomento non è definito, il *pcbErrorMsg* argomento è uguale a 0, e il *lpszErrorMsg* argomento contiene un singolo carattere di terminazione null (a meno che il *cbErrorMsgMax* argomento è uguale a 0).
