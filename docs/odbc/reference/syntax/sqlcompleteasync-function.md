---
title: Funzione SQLCompleteAsync | Documenti Microsoft
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
f1_keywords:
- SQLCompleteAsync
helpviewer_keywords:
- SQLCompleteAsync function [ODBC]
ms.assetid: 1b97c46a-d2e5-4540-8239-9d975e5321c6
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 91a6449e07ff83fd6bb7478bfc52cb077a76c955
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlcompleteasync-function"></a>SQLCompleteAsync (funzione)
**Conformità**  
 Introdotta: versione ODBC 3.8  
  
 Conformità agli standard: nessuno  
  
 **Riepilogo**  
 **SQLCompleteAsync** può essere utilizzato per determinare quando una funzione asincrona viene completata utilizzando l'elaborazione basata su notifica o polling. Per ulteriori informazioni sulle operazioni asincrone, vedere [esecuzione asincrona](../../../odbc/reference/develop-app/asynchronous-execution.md).  
  
 **SQLCompleteAsync** è implementata solo in Gestione Driver ODBC.  
  
 In modalità di elaborazione asincrona di notifica in base **SQLCompleteAsync** deve essere chiamato dopo che il Driver Manager genera l'oggetto evento utilizzato per la notifica. **SQLCompleteAsync** completamento asincrona l'elaborazione e la funzione asincrona verrà generato un codice restituito.  
  
 In modalità di elaborazione asincrona di polling in base **SQLCompleteAsync** è un'alternativa alla chiamata della funzione asincrona originale, senza la necessità di specificare gli argomenti nella chiamata di funzione asincrona originale. **SQLCompleteAsync** può essere usata indipendentemente dal fatto che, se è abilitata la libreria di cursori ODBC.  
  
## <a name="syntax"></a>Sintassi  
  
```vb  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>Argomenti  
 *HandleType*  
 [Input] L'elaborazione del tipo di handle sul quale completare asincrona. I valori validi sono impostato su SQL_HANDLE_DBC o impostato su SQL_HANDLE_STMT.  
  
 *Handle*  
 [Input] L'handle sul quale completare asincrona l'elaborazione. Se *gestire* non è un handle valido del tipo specificato da *HandleType*, **SQLCompleteAsync** restituisca SQL_INVALID_HANDLE.  
  
 Se *gestire* non è un handle valido del tipo specificato da *HandleType*, **SQLCompleteAsync** restituisca SQL_INVALID_HANDLE.  
  
 *AsyncRetCodePtr*  
 [Output] Puntatore a un buffer che conterrà il codice restituito dell'API asincrona. Se *AsyncRetCodePtr* è NULL, **SQLCompleteAsync** restituisce SQL_ERROR.  
  
## <a name="returns"></a>Valori di codice restituiti  
 SQL_SUCCESS, SQL_ERROR, SQL_NO_DATA o SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostica  
 Se **SQLCompleteAsync** restituisce SQL_SUCCESS, un'applicazione devono ricevere il codice restituito della funzione asincrona dal buffer a cui puntava *AsyncRetCodePtr*. SQLSTATE associato, se presente, può essere ottenuto chiamando **SQLGetDiagRec** con un *HandleType* impostato su SQL_HANDLE_STMT e un handle di istruzione o un *HandleType* di SQL _ HANDLE_DBC e un handle di connessione. Tali record di diagnostica associati con la funzione asincrona, questo non **SQLCompleteAsync** (funzione).  
  
 **SQLCompleteAsync** restituisce un codice diverso da SQL_SUCCESS per indicare che **SQLCompleteAsync** non viene chiamato correttamente. **SQLCompleteAsync** non invierà alcun record di diagnostica in questo caso. Sono possibili codici restituiti:  
  
-   SQL_INVALID_HANDLE: L'handle indicato da *HandleType* e *gestire* non è un handle valido.  
  
-   SQL_ERROR: *AsyncRetCodePtr* è NULL o non è abilitato l'elaborazione asincrona dell'handle.  
  
-   SQL_NO_DATA: In modalità di notifica, un'operazione asincrona non è in corso o in Gestione Driver ha non riceve una notifica all'applicazione. In modalità di polling, un'operazione asincrona non è in corso.  
  
## <a name="comments"></a>Commenti  
 In modalità di elaborazione asincrona di polling in base *AsyncRetCodePtr* potrebbe essere SQL_STILL_EXECUTING quando **SQLCompleteAsync** restituisce SQL_SUCCESS. Applicazione deve mantenere il polling finché *AsyncRetCodePtr* non SQL_STILL_EXECUTING. In modalità di elaborazione asincrona di notifica in base *AsyncRetCodePtr* non potranno mai essere SQL_STILL_EXECUTING.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione asincrona (metodo di polling)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
