---
title: Funzione SQLPostInstallerError | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLPostInstallerError
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLPostInstallerError
helpviewer_keywords: SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1071ffc1b7429cd8518e4581bba2271a4ccd81ba
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.0  
  
 **Riepilogo**  
 **SQLPostInstallerError** fornisce un meccanismo per una libreria di programma di installazione driver o funzione di conversione per segnalare gli errori di **ConfigDriver**, **ConfigDSN**, e **ConfigTranslator del**  funzioni nella coda degli errori di programma di installazione. Le applicazioni non utilizzano questa API. usano **SQLInstallerError** per recuperare l'errore.  
  
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
