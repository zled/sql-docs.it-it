---
title: Driver di Database di diagnostica per Desktop | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], diagnostic information
- desktop database drivers [ODBC], diagnostic information
- ODBC desktop database drivers [ODBC], diagnostic information
- diagnostic information [ODBC], desktop database drivers
ms.assetid: 1c3740eb-62c6-4009-b4b2-570fcf5661e4
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2295462d7ec6e2e11f9eb43ada5617660bf955ca
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="diagnostics-for-desktop-database-drivers"></a>Diagnostica per i Database Desktop driver
Tutti gli errori e avvisi non selezionato o parzialmente controllata da Gestione Driver vengono gestiti dal driver. Il driver esegue il mapping anche native errori o gli errori restituiti dall'origine dati, di SQLSTATE. Ogni funzione nel *riferimento per programmatori ODBC* contiene una sezione "Diagnostics" che specifica le condizioni e i messaggi.  
  
 Le applicazioni chiamano **SQLGetDiagRec** per recuperare i messaggi di diagnostica, codice di errore nativo e SQLSTATE. La chiamata **SQLGetDiagField** e specificando il campo recupera singoli campi di diagnostica. Il livello di supporto degli identificatori di diagnostica è elencato nella tabella seguente.  
  
|DiagIdentifiers|Livello di supporto|  
|---------------------|-------------------|  
|SQL_DIA_DYNAMIC_FUNCTION|Non supportato|  
|SQL_DIAG_CLASS_ORIGIN|Supportato. Sempre "ODBC 3.0" per le versioni 3.0 e versioni successive di questo driver.|  
|SQL_DIAG_COLUMN_NUMBER|Supportato|  
|SQL_DIAG_CURSOR_ROW_COUNT|Non supportato|  
|SQL_DIAG_DYNAMIC_FUNCTION_CODE|Non supportato|  
|SQL_DIAG_MESSAGE_TEXT|Supportato|  
|SQL_DIAG_NATIVE|Supportato|  
|SQL_DIAG_NUMBER|Supportato|  
|SQL_DIAG_RETURNCODE|Supportato ma implementato da Gestione Driver|  
|SQL_DIAG_ROW_COUNT|Supportato|  
|SQL_DIAG_ROW_NUMBER|Supportato|  
|SQL_DIAG_SERVER_NAME|Non supportato|  
|SQL_DIAG_SQLSTATE|Supportato|  
|SQL_DIAG_SUBCLASS_ORIGIN|Supportato|
