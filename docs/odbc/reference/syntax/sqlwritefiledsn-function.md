---
title: Funzione SQLWriteFileDSN | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLWriteFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteFileDSN
helpviewer_keywords:
- SQLWriteFileDSN [ODBC]
ms.assetid: 9e18f56f-1061-416b-83d4-ffeec42ab5a9
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 36af0a5a3098dd4afc334de6bd808c0c690a601c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32918276"
---
# <a name="sqlwritefiledsn-function"></a>Funzione SQLWriteFileDSN
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLWriteFileDSN** scrive le informazioni in un DSN su File.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszFileName*  
 [Input] Puntatore al nome di DSN su File. Un'estensione per il DSN viene aggiunto a tutti i nomi di file che non dispongono già di un'estensione per il DSN.  
  
 *lpszAppName*  
 [Input] Puntatore al nome dell'applicazione. Questo è "ODBC" per la sezione ODBC.  
  
 *lpszkeyname stringa*  
 [Input] Puntatore al nome della chiave da leggere. Per parole chiave riservate, vedere "Commenti".  
  
 *lpszString*  
 [Output] A cui punta la stringa associata con la chiave da scrivere. La lunghezza massima della stringa a cui fa riferimento in questo argomento è 32.767 byte.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLWriteFileDSN** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_PATH|Percorso di installazione non valido.|Il percorso del nome file specificato nella *lpszFileName* argomento non valido.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Tipo di richiesta non valido|Il *lpszAppName*, *lpszkeyname stringa*, o *lpszString* argomento è NULL.|  
  
## <a name="comments"></a>Commenti  
 ODBC si riserva il nome della sezione [ODBC] in cui archiviare le informazioni di connessione. Le parole chiave riservate di questa sezione sono gli stessi quelli riservati per una stringa di connessione in **SQLDriverConnect**. (Per ulteriori informazioni, vedere il [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) descrizione della funzione.)  
  
 Le applicazioni è possono utilizzare queste parole chiave riservate per scrivere informazioni direttamente in un DSN su File. Se un'applicazione si desidera creare o modificare la stringa di connessione senza DSN associata a un DSN su File, è possibile chiamare **SQLWriteFileDSN** per le parole chiave della stringa di connessione riservate nella sezione [ODBC].  
  
 Se il *lpszString* argomento è un puntatore null, la parola chiave a cui fa riferimento il *lpszkeyname stringa* argomento verrà eliminato dal file DSN. Se il *lpszString* e *lpszkeyname stringa* gli argomenti sono entrambi puntatori null, la sezione a cui fa riferimento il *lpszAppName* argomento verrà eliminato dal file DSN.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Lettura delle informazioni da DSN su File|[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|
