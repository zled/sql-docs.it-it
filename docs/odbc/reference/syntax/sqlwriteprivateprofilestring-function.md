---
title: Funzione SQLWritePrivateProfileString | Documenti Microsoft
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
- SQLWritePrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWritePrivateProfileString
helpviewer_keywords:
- SQLWritePrivateProfileString [ODBC]
ms.assetid: 526f36a4-92ed-4874-9725-82d27c0b86f9
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd2ef7d8e5fdab610c5bc37f9e58c1dd031b80e9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlwriteprivateprofilestring-function"></a>SQLWritePrivateProfileString (funzione)
**Conformità**  
 Introdotta: versione ODBC 2.0  
  
 **Riepilogo**  
 **SQLWritePrivateProfileString** scrive un nome di valore e i dati per la sottochiave ini le informazioni di sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLWritePrivateProfileString(  
     LPCSTR     lpszSection,  
     LPCSTR     lpszEntry,  
     LPCSTR     lpszString,  
     LPCSTR     lpszFilename);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszSection*  
 [Input] Punta a una stringa con terminazione null contenente il nome della sezione in cui verrà copiata la stringa. Se la sezione non esiste, viene creato. Il nome della sezione è indipendente dalla case. la stringa può essere qualsiasi combinazione di lettere maiuscole e minuscole.  
  
 *lpszEntry*  
 [Input] Punta a una stringa con terminazione null contenente il nome della chiave da associare a una stringa. Se la chiave non esiste nella sezione specificata, viene creato. Se questo argomento è NULL, l'intera sezione, incluse tutte le voci all'interno della sezione, viene eliminato.  
  
 *lpszString*  
 [Input] Punta a una stringa con terminazione null da scrivere nel file. Se questo argomento è NULL, la chiave a cui punta il *lpszEntry* argomento è stato eliminato.  
  
 *lpszFilename*  
 [Output] Punta a una stringa con terminazione null che il nome del file di inizializzazione.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLWritePrivateProfileString** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_REQUEST_FAILED|Richiesta non riuscita|Impossibile scrivere le informazioni di sistema richiesta.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLWritePrivateProfileString** viene fornito come un modo semplice per i driver di porta e l'installazione di driver DLL da Microsoft® Windows® per Microsoft Windows/Windows 2000. Le chiamate a **WritePrivateProfileString** che scrivere una stringa di profilo per il file Odbc.ini deve essere sostituita con chiamate a **SQLWritePrivateProfileString**. **SQLWritePrivateProfileString** chiama le funzioni nell'API Win32® per aggiungere il nome del valore specificato e i dati per la sottochiave ini le informazioni di sistema.  
  
 Una modalità di configurazione indica la voce Odbc.ini Elenco valori DSN nelle informazioni di sistema. Se il DSN è un DSN utente (la variabile di stato è USERDSN_ONLY), la funzione scrive la voce di ODBC in HKEY_CURRENT_USER. Se il DSN è un DSN di sistema (SYSTEMDSN_ONLY), la funzione scrive la voce Odbc.ini nella chiave HKEY_LOCAL_MACHINE. Se la variabile di stato è BOTHDSN, viene eseguito un tentativo di HKEY_CURRENT_USER e in caso contrario, viene utilizzato HKEY_LOCAL_MACHINE.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Ottiene un valore dalle informazioni di sistema|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
