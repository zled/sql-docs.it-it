---
title: Funzione SQLGetPrivateProfileString | Documenti Microsoft
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
- SQLGetPrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetPrivateProfileString
helpviewer_keywords:
- SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e970b4d3e087e2df4043a36f1fe2881680cf7d3b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetprivateprofilestring-function"></a>SQLGetPrivateProfileString (funzione)
**Conformità**  
 Introdotta: versione ODBC 2.0  
  
 **Riepilogo**  
 **SQLGetPrivateProfileString** Ottiene un elenco di nomi di valori o dati corrispondenti a un valore delle informazioni sul sistema.  
  
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
 [Input] Punta alla stringa con terminazione null contenente il nome della chiave è necessario recuperare il cui stringa associata. Se questo argomento è NULL, tutti i nomi di sezione specificata da della chiave di *lpszSection* argomento vengono copiati nel buffer specificato per il *RetBuffer* argomento.  
  
 *lpszDefault*  
 [Input] Punta a una stringa con terminazione null che specifica il valore predefinito per la chiave specificata, se la chiave non viene trovata nel file di inizializzazione. Questo argomento non può essere NULL.  
  
 *RetBuffer*  
 [Output] Punta al buffer che riceve la stringa recuperata.  
  
 *cbRetBuffer*  
 [Input] Specifica la dimensione, in caratteri, del buffer a cui fa riferimento il *RetBuffer* argomento.  
  
 *lpszFilename*  
 [Input] Punta a una stringa con terminazione null che il nome del file di inizializzazione. Se questo argomento non contiene un percorso completo del file, la directory predefinita viene eseguita la ricerca.  
  
## <a name="returns"></a>Valori di codice restituiti  
 **SQLGetPrivateProfileString** restituisce un valore intero che indica il numero di caratteri letti.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando una chiamata a **SQLGetPrivateProfileString** non riesce, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore di programma di installazione generale|Si verificato un errore per cui si è verificato alcun errore di programma di installazione specifico.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 **SQLGetPrivateProfileString** viene fornito come un modo semplice per i driver di porta e l'installazione di driver DLL da Microsoft® Windows® per Microsoft Windows/Windows 2000. Le chiamate a **GetPrivateProfileString** che recuperano una stringa di profilo nel file Odbc.ini deve essere sostituita con chiamate a **SQLGetPrivateProfileString**. **SQLGetPrivateProfileString** chiama le funzioni nell'API Win32® per recuperare i nomi richiesti di valori o i dati corrispondenti a un valore della sottochiave ini le informazioni di sistema.  
  
 La modalità di configurazione (come impostato dalla **SQLSetConfigMode**) indica la posizione nelle informazioni di sistema la voce Odbc.ini Elenco valori DSN. Se il DSN è un DSN utente (la modalità di configurazione è USERDSN_ONLY), la funzione legge dalla voce di ODBC in HKEY_CURRENT_USER. Se il DSN è un DSN di sistema (SYSTEMDSN_ONLY), la funzione legge dalla voce di ODBC in HKEY_LOCAL_MACHINE. Se la modalità di configurazione è BOTHDSN, viene eseguito un tentativo di HKEY_CURRENT_USER e in caso contrario, viene utilizzato HKEY_LOCAL_MACHINE.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Scrive un valore per le informazioni di sistema|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
