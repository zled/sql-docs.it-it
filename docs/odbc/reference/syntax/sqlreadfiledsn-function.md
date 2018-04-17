---
title: Funzione SQLReadFileDSN | Documenti Microsoft
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
- SQLReadFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLReadFileDSN
helpviewer_keywords:
- SQLReadFileDSN function [ODBC]
ms.assetid: ead464aa-cdc3-47dd-a0c0-997711205d31
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1db13b239a2cf9e1f121336e792333b70f042ed8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlreadfiledsn-function"></a>SQLReadFileDSN (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLReadFileDSN** legge le informazioni da un DSN su File.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLReadFileDSN(  
     LPCSTR   lpszFileName,  
     LPCSTR   lpszAppName,  
     LPCSTR   lpszKeyName,  
     LPSTR    lpszString,  
     WORD     cbString,  
     WORD *   pcbString);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszFileName*  
 [Input] Puntatore al buffer di dati che contiene il nome del file DSN. Un'estensione per il DSN viene aggiunto a tutti i nomi di file che non dispongono già di un'estensione per il DSN. Il valore in  *\*lpszFileName* deve essere una stringa con terminazione null.  
  
 *lpszAppName*  
 [Input] Puntatore al buffer di dati che contiene il nome dell'applicazione. Questo è "ODBC" per la sezione ODBC. Il valore in  *\*lpszAppName* deve essere una stringa con terminazione null.  
  
 *lpszkeyname stringa*  
 [Input] Puntatore al buffer di dati che contiene il nome della chiave da leggere. Per parole chiave riservate, vedere "Commenti". Il valore in  *\*lpszAppName* deve essere una stringa con terminazione null.  
  
 *lpszString*  
 [Output] Puntatore al buffer di dati che contiene la stringa associata alla chiave per la lettura.  
  
 Se  *\*lpszFileName* è un nome DSN valido, ma il *lpszAppName* argomento è un puntatore null e *lpszkeyname stringa* argomento è un puntatore null, il  *\*lpszString* contiene un elenco di applicazioni valide. Se  *\*lpszFileName* è un nome di file valido. DSN e  *\*lpszAppName* è un nome di applicazione valido, ma la *lpszkeyname stringa* argomento è un valore null puntatore, quindi  *\*lpszString* contiene un elenco di parole chiave riservate valide nella sezione appropriata del file DSN, delimitata da punti e virgola. Se  *\*lpszFileName* è un nome DSN valido ma  *\*lpszAppName* è un puntatore null e *lpszkeyname stringa* argomento è un puntatore null, quindi  *\*lpszString* contiene un elenco di sezioni nel file DSN, delimitate da punti e virgola.  
  
 *cbString*  
 [Input] Lunghezza di  *\*lpszString* buffer.  
  
 *pcbString*  
 [Output] Numero totale di byte disponibili per restituire  *\*lpszString*. Se il numero di byte disponibili da restituire è maggiore o uguale a *cbString*, la stringa di output in  *\*lpszString* viene troncato a *cbString* meno il carattere di terminazione null. Il *pcbString* argomento può essere un puntatore null.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLReadFileDSN** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Lunghezza del buffer non valido|Il *lpszString* argomento è NULL.<br /><br /> Il *cbString* argomento è minore o uguale a 0.|  
|ODBC_ERROR_INVALID_PATH|Percorso di installazione non valido.|Il percorso del nome file specificato nella *lpszFileName* argomento non valido.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Tipo di richiesta non valido|Il *lpszAppName* argomento è NULL, mentre il *lpszkeyname stringa* argomento è valido.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|Stringa di output troncato|La stringa restituita  *\*lpszString* è stato troncato perché il valore in *cbString* è minore o uguale al valore di stato  *\*pcbString*.|  
|ODBC_ERROR_REQUEST_FAILED|Richiesta non riuscita|La parola chiave non esiste nel file DSN.|  
  
## <a name="comments"></a>Commenti  
 ODBC si riserva il nome della sezione [ODBC] in cui archiviare le informazioni di connessione. Le parole chiave riservate di questa sezione sono gli stessi quelli riservati per una stringa di connessione in **SQLDriverConnect**. (Per ulteriori informazioni, vedere il [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) descrizione della funzione.)  
  
 Le applicazioni è possono utilizzare queste parole chiave riservate per leggere le informazioni in un DSN su File. Se un'applicazione desidera scoprire la stringa di connessione senza DSN associata a un DSN su File, è possibile chiamare **SQLReadFileDSN** per le parole chiave della stringa di connessione riservate nella sezione [ODBC]. La stringa di connessione completa passata in una connessione senza DSN è una combinazione di tutte le parole chiave (riservate e specifici del driver) nella sezione [ODBC].  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Scrittura di informazioni in un DSN su File|[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|
