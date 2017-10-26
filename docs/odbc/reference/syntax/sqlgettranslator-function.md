---
title: Funzione SQLGetTranslator | Documenti Microsoft
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
- SQLGetTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTranslator
helpviewer_keywords:
- SQLGetTranslator function [ODBC]
ms.assetid: 33879db3-5ef9-4585-9be5-69376157e017
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 76bc8c85e923c792e87c13c2ca7f490c7273d975
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgettranslator-function"></a>SQLGetTranslator (funzione)
**Conformità**  
 Introdotta: versione ODBC 2.0  
  
 **Riepilogo**  
 **SQLGetTranslator** Visualizza una finestra di dialogo da cui un utente può selezionare una funzione di conversione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLGetTranslator(  
     HWND      hwndParent,  
     LPSTR     lpszName,  
     WORD      cbNameMax,  
     WORD *    pcbNameOut,  
     LPSTR     lpszPath,  
     WORD      cbPathMax,  
     WORD *    pcbPathOut,  
     DWORD *   pvOption);  
```  
  
## <a name="arguments"></a>Argomenti  
 *hwndParent*  
 [Input] Handle della finestra padre.  
  
 *lpszName*  
 [Input/Output] Nome della funzione di conversione dalle informazioni di sistema.  
  
 *cbNameMax*  
 [Input] Lunghezza massima del *lpszName* buffer.  
  
 *pcbNameOut*  
 [Input/Output] Numero totale di byte (escluso il byte di terminazione null) passate o restituite *lpszName*. Se il numero di byte disponibili da restituire è maggiore o uguale a *cbNameMax*, il nome della funzione di conversione in *lpszName* viene troncato a *cbNameMax* meno il carattere di terminazione null. Il *pcbNameOut* argomento può essere un puntatore null.  
  
 *lpszPath*  
 [Output] Percorso completo della DLL di conversione.  
  
 *cbPathMax*  
 [Input] Lunghezza massima del *lpszPath* buffer.  
  
 *pcbPathOut*  
 [Output] Numero totale di byte (escluso il byte di terminazione null) restituito in *lpszPath*. Se il numero di byte disponibili da restituire è maggiore o uguale a *cbPathMax*, il percorso della DLL di conversione in *lpszPath* viene troncato a *cbPathMax* meno il carattere di terminazione null. Il *pcbPathOut* argomento può essere un puntatore null.  
  
 *pvOption*  
 Opzione di conversione a 32 bit [output].  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore o se l'utente annulla la finestra di dialogo.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetTranslator** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Lunghezza del buffer non valido|Il *cbNameMax* o *cbPathMax* argomento è minore o uguale a 0.|  
|ODBC_ERROR_INVALID_HWND|Handle di finestra non valido.|Il *hwndParent* argomento non valido o NULL.|  
|ODBC_ERROR_INVALID_NAME|Nome del driver o funzione di conversione non valido|Il *lpszName* argomento non valido. Non è stato possibile trovarlo nel Registro di sistema.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Non è stato possibile caricare la libreria dell'installazione del driver o funzione di conversione|Impossibile caricare la libreria di conversione.|  
|ODBC_ERROR_INVALID_OPTION|Opzione di transazione non valido|Il *pvOption* argomento è contenuto un valore non valido.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 Se *hwndParent* è null o se *lpszName*, *lpszPath*, o *pvOption* è un puntatore null, **SQLGetTranslator** restituisce FALSE. In caso contrario, viene visualizzato l'elenco di funzioni di conversione installati nella finestra di dialogo seguente.  
  
 ![Finestra di dialogo Seleziona convertitore](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Se *lpszName* contiene un nome valido di funzione di conversione, questa opzione è selezionata. In caso contrario, \<Nessun convertitore > sia selezionata.  
  
 Se l'utente sceglie \<Nessun convertitore >, il contenuto di *lpszName*, *lpszPath*, e *pvOption* non sono interessate. **SQLGetTranslator** imposta *pcbNameOut* e *pcbPathOut* a 0 e restituisce TRUE.  
  
 Se l'utente sceglie una funzione di conversione, **SQLGetTranslator** chiamate **ConfigTranslator del** nel programma di installazione del convertitore. DLL. Se **ConfigTranslator del** restituisce FALSE, **SQLGetTranslator** restituisce per la finestra di dialogo. Se **ConfigTranslator del** restituisce TRUE, **SQLGetTranslator** restituisce TRUE, insieme all'opzione di conversione, il percorso e nome traduttore selezionato.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Configurazione di una funzione di conversione|[ConfigTranslator del](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Recupero di un attributo di traduzione|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|L'impostazione di un attributo di traduzione|[Funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|

