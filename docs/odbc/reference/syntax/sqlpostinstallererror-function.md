---
title: Funzione SQLPostInstallerError | Documenti Microsoft
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
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f7d3a6bec7c12e271c073d5665c0a4e9b227ceef
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLPostInstallerError** fornisce un meccanismo per una libreria di programma di installazione driver o funzione di conversione per segnalare gli errori di **ConfigDriver**, **ConfigDSN**, e **ConfigTranslator del ** funzioni nella coda degli errori di programma di installazione. Le applicazioni non utilizzano questa API. usano **SQLInstallerError** per recuperare l'errore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Argomenti  
 *fErrorCode*  
 [Input] Codice di errore di programma di installazione.  
  
 *szErrorMsg*  
 [Input] Testo del messaggio di errore.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS o SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostica  
 **SQLPostInstallerError** non registrare i valori di errore per se stesso. Se l'errore è stato registrato correttamente nella coda degli errori di programma di installazione (recuperabili tramite **SQLInstallerError**), viene restituito SQL_SUCCESS. Verrà restituito SQL_ERROR se il valore di *dwErrorCode* argomento non è uno dei codici di errore di programma di installazione specificato.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un driver|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Aggiunta, modifica o rimozione di origini dati|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|L'impostazione di un'opzione di conversione|[ConfigTranslator del](../../../odbc/reference/syntax/configtranslator-function.md)|

