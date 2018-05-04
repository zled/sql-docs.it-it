---
title: Funzione SQLPostInstallerError | Documenti Microsoft
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
ms.topic: conceptual
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
manager: craigg
ms.openlocfilehash: 5ff4ce6578c2f62b840129f474b4a2aed7d1ff5b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLPostInstallerError** fornisce un meccanismo per una libreria di programma di installazione driver o funzione di conversione per riportare errori per il **ConfigDriver**, **ConfigDSN**, e **ConfigTranslator del**  funzioni alla coda di errore di programma di installazione. Le applicazioni non utilizzano questa API. usano **SQLInstallerError** per recuperare l'errore.  
  
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
