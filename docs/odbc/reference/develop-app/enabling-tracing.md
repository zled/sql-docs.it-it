---
title: Abilitazione della traccia | Documenti Microsoft
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
helpviewer_keywords: tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 569c5b42c57bca4eff30225f5dcc1ff1176fe00e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="enabling-tracing"></a>Abilitazione della traccia
La traccia può essere abilitata come indicato di seguito in tre modi:  
  
-   Impostare il **traccia** e **TraceFile** parole chiave nella voce del Registro di sistema ODBC. Questo Abilita o disabilita la traccia quando **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_ENV viene chiamato. Queste opzioni vengono impostate nella scheda analisi della finestra di dialogo Amministratore origine dati ODBC visualizzata durante l'installazione di origine dati. Per ulteriori informazioni, vedere [le voci del Registro di sistema per le origini dati](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Chiamare **SQLSetConnectAttr** per impostare l'attributo di connessione SQL_ATTR_TRACE SQL_OPT_TRACE_ON. Questo Abilita o disabilita la traccia per la durata della connessione. Per ulteriori informazioni, vedere il [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) descrizione della funzione.  
  
-   Utilizzare **ODBCSharedTraceFlag** per attivare o disattivare la traccia in modo dinamico. (Per ulteriori informazioni, vedere l'argomento successivo, [analisi dinamica](../../../odbc/reference/develop-app/dynamic-tracing.md).)
