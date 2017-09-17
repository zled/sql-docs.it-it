---
title: SQLSetStmtOption (Driver ODBC di Visual FoxPro) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 76b813e3-c7dc-4bb2-a710-d2aa9dcfdc36
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9374aed937aed17c0e1157eb6523f9b313473698
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetstmtoption-visual-foxpro-odbc-driver"></a>SQLSetStmtOption (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Livello 1  
  
 Imposta le opzioni relative a un handle di istruzione, *hstmt*.  
  
|*fOption*|Valori consentiti|Commenti|  
|---------------|--------------------|--------------|  
|SQL_ASYNC_ENABLE|SQL_ASYNC_ENABLE_OFF|Se si tenta di impostare questo valore *fOption*, il driver restituisce l'errore: "Driver non valido". Visual FoxPro non supporta l'esecuzione asincrona.|  
|SQL_BIND_TYPE|SQL_BIND_BY_COLUMN o un valore a 32 bit che indica la lunghezza della struttura o un'istanza di un buffer in cui verranno associate colonne.||  
|SQL_CONCURRENCY|SQL_CONCUR_READ_ONLY<br /><br /> SQL_CONCUR_LOCK<br /><br /> SQL_CONCUR_VALUES|Il driver non consente SQL_CONCUR_ROWVER, perché Visual FoxPro non dispone delle versioni delle righe basata sui timestamp.|  
|SQL_CURSOR_TYPE|SQL_CURSOR_FORWARD_ONLY<br /><br /> SQL_CURSOR_STATIC|Il driver non è possibile SQL_CURSOR_KEYSET_DRIVEN o SQL_CURSOR_DYNAMIC; vedere [SQLSetScrollOptions](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md) per ulteriori informazioni.|  
|SQL_KEYSET_SIZE|Errore: "Driver non valido"|Visual FoxPro non supporta il modello di cursore keyset.|  
|SQL_MAX_LENGTH|0|Se si tenta di impostare questo valore *fOption* valore, il driver restituisce l'errore "Driver non valido".|  
|SQL_MAX_ROWS|0|Se si tenta di impostare questo valore *fOption* valore, il driver restituisce l'errore "Driver non valido".|  
|SQL_NOSCAN|SQL_NOSCAN_OFF||  
|SQL_QUERY_TIMEOUT|0|Se si tenta di impostare questo valore *fOption* valore, il driver restituisce l'errore "Driver non valido".|  
|SQL_RETRIEVE_DATA|SQL_RD_ON, SQL_RD_OFF||  
|SQL_ROWSET_SIZE|da 1 a 4.294.967.296||  
|SQL_SIMULATE_CURSOR|Errore: "Driver non valido"||  
|SQL_USE_BOOKMARKS|SQL_UB_OFF<br /><br /> SQL_UB_ON||  
  
 Per ulteriori informazioni, vedere [SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md) nel *riferimento per programmatori ODBC*.
