---
title: Funzione SQLGetPrivateProfileString | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetPrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetPrivateProfileString
helpviewer_keywords:
- SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9790305690b83e5e5a39e8f645a419c8ddd098b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640630"
---
# <a name="sqlgetprivateprofilestring-function"></a>Funzione SQLGetPrivateProfileString
**Conformità**  
 Versione introdotta: ODBC 2.0  
  
 **Riepilogo**  
 **SQLGetPrivateProfileString** Ottiene un elenco di nomi di valori o i dati corrispondenti a un valore delle informazioni sul sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int SQLGetPrivateProfileString(  
     LPCSTR   lpszSection,  
     LPCSTR   lpszEntry,  
     LPCSTR   lpszDefault,  
     LPCSTR   RetBuffer,  
     INT      cbRetBuffer,  
     LPCSTR   lpszFilename);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszSection*  
 [Input] Punta a una stringa con terminazione null che specifica la sezione che contiene il nome della chiave. Se questo argomento è NULL, la funzione Copia tutti i nomi di sezione nel file per il buffer fornito.  
  
 *lpszEntry*  
 [Input] Punta alla stringa con terminazione null che contiene il nome della chiave la cui stringa associata viene da recuperare. Se questo argomento è NULL, tutte le chiavi nella sezione specificata da nomi di *lpszSection* argomento vengono copiati nel buffer specificato dal *RetBuffer* argomento.  
  
 *lpszDefault*  
 [Input] Punta a una stringa con terminazione null che specifica il valore predefinito per la chiave specificata se la chiave non viene trovata nel file di inizializzazione. Questo argomento non può essere NULL.  
  
 *RetBuffer*  
 [Output] Punta al buffer che riceve la stringa recuperata.  
  
 *cbRetBuffer*  
 [Input] Specifica la dimensione, in caratteri, del buffer a cui fa riferimento il *RetBuffer* argomento.  
  
 *lpszFilename*  
 [Input] Punta a una stringa con terminazione null che corrisponde al nome del file di inizializzazione. Se questo argomento non contiene un percorso completo del file, viene eseguita la ricerca nella directory predefinita.  
  
## <a name="returns"></a>Valori di codice restituiti  
 **SQLGetPrivateProfileString** restituisce un valore integer che indica il numero di caratteri letti.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando una chiamata a **SQLGetPrivateProfileString** ha esito negativo, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* i valori che possono essere restituiti da **SQLInstallerError** e illustra ognuna nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione non è stato possibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLGetPrivateProfileString** viene fornito come un modo semplice per la porta driver e file DLL di installazione di driver di Microsoft® Windows® per Microsoft Windows/Windows 2000. Le chiamate a **GetPrivateProfileString** che recuperano una stringa di profilo dal file ini deve essere sostituita con le chiamate a **SQLGetPrivateProfileString**. **SQLGetPrivateProfileString** chiama le funzioni nell'API Win32® per recuperare i nomi richiesti di valori o i dati corrispondenti a un valore della sottochiave ODBC. ini delle informazioni di sistema.  
  
 La modalità di configurazione (come impostato da **SQLSetConfigMode**) indica se la voce ini Elenca i valori DSN è nelle informazioni di sistema. Se il DSN è un DSN utente (la modalità di configurazione è USERDSN_ONLY), la funzione legge dalla voce ini in HKEY_CURRENT_USER. Se il DSN è un DSN di sistema (SYSTEMDSN_ONLY), la funzione legge dalla voce ini in HKEY_LOCAL_MACHINE. Se la modalità di configurazione è BOTHDSN, viene eseguito un tentativo di HKEY_CURRENT_USER e, se ha esito negativo, HKEY_LOCAL_MACHINE viene usato.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Scrive un valore per le informazioni di sistema|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
