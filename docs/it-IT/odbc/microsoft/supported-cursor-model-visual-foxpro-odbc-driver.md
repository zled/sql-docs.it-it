---
title: È supportato il modello di cursore, Driver ODBC di Visual FoxPro | Documenti Microsoft
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
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], cursors
- cursors [ODBC], Visual FoxPro ODBC driver
- FoxPro ODBC driver [ODBC], cursors
- static cursors [ODBC]
- block cursors [ODBC]
- rowset cursors [ODBC]
ms.assetid: be95bbb2-6886-491e-a5a7-f58028d19c1e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc90ecf57553feb7913986994e9f28dfe7050eea
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supported-cursor-model-visual-foxpro-odbc-driver"></a>Modello di cursore supportati (Driver ODBC di Visual FoxPro)
Il Driver ODBC di Visual FoxPro supporta sia *blocco* (*set di righe*) e *statico* cursori. I cursori statici sono supportati per un driver conforme alla conformità di livello 1 ODBC. Il driver non supporta dynamic, basati su keyset o misto (keyset e dynamic) i cursori.  
  
 L'applicazione può chiamare [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) con un'opzione SQL_CURSOR_TYPE di SQL_CURSOR_FORWARD_ONLY (cursore a blocchi) o SQL_CURSOR_STATIC (cursore statico).  
  
> [!NOTE]  
>  Se si chiama **SQLSetStmtOption** con un'opzione SQL_CURSOR_TYPE diverso da SQL_CURSOR_FORWARD_ONLY o SQL_CURSOR_STATIC, la funzione restituisce SQL_SUCCESS_WITH_INFO con un valore SQLSTATE di 01S02 (valore di opzione modificato). Il driver imposta SQL_CURSOR_STATIC tutte le modalità di cursore non supportato.  
  
 Per ulteriori informazioni sui tipi di cursore e circa **SQLSetStmtOption**, vedere il [riferimento per programmatori ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="block-cursor"></a>cursore rettangolare  
 Un set di risultati lo scorrimento in avanti di sola lettura restituito al client, che è responsabile della gestione archiviazione per i dati.  
  
## <a name="static-cursor"></a>cursore statico  
 Uno snapshot di un set di dati definito dalla query. I cursori statici non riflettono le modifiche in tempo reale dei dati sottostanti da altri utenti. Buffer di memoria del cursore viene mantenuto dalla libreria di cursori ODBC, che consente lo scorrimento in avanti e indietro.  
  
## <a name="rowset"></a>set di righe  
 Blocchi di dati archiviati in un cursore, che rappresenta le righe recuperate da un'origine dati.
