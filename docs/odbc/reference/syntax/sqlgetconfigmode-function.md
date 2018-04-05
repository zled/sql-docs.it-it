---
title: Funzione SQLGetConfigMode | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca766c5cb2e619672193888c791d4dee13a029e8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetconfigmode-function"></a>SQLGetConfigMode (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLGetConfigMode** recupera la modalità di configurazione che indica la posizione nelle informazioni di sistema la voce Odbc.ini Elenco valori DSN.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Argomenti  
 *pwConfigMode*  
 [Output] Puntatore al buffer che contiene la modalità di configurazione. (Vedere "Commenti".) Il valore in  *\*pwConfigMode* può essere:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di errore.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLGetConfigMode** restituisce FALSE, un oggetto associato  *\*pfErrorCode* valore può essere ottenuto chiamando **SQLInstallerError**. La tabella seguente elenca i  *\*pfErrorCode* valori che possono essere restituiti da **SQLInstallerError** e illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione: Impossibile eseguire la funzione a causa della mancanza di memoria.|  
  
## <a name="comments"></a>Commenti  
 Questa funzione viene utilizzata per determinare la posizione nelle informazioni di sistema la voce Odbc.ini Elenco valori DSN. Se  *\*pwConfigMode* ODBC_USER_DSN, il DSN è un DSN utente e la funzione legge dalla voce di ODBC in HKEY_CURRENT_USER. Se è ODBC_SYSTEM_DSN, il DSN è un DSN di sistema e la funzione legge dalla voce di ODBC in HKEY_LOCAL_MACHINE. Se è ODBC_BOTH_DSN, viene eseguito un tentativo di HKEY_CURRENT_USER e in caso contrario, viene utilizzato HKEY_LOCAL_MACHINE.  
  
 Per impostazione predefinita, **SQLGetConfigMode** restituisce ODBC_BOTH_DSN. Quando viene creato un DSN utente o un DSN di sistema da una chiamata a **SQLConfigDataSource**, la funzione imposta la modalità di configurazione su ODBC_USER_DSN o ODBC_SYSTEM_DSN per distinguere i DSN di sistema e utente durante la modifica di un DSN. Prima della restituzione, **SQLConfigDataSource** ODBC_BOTH_DSN Reimposta la modalità di configurazione.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|L'impostazione della modalità di configurazione|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|
