---
title: Analisi dinamica | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 51ea74b8b54bf9d9e26bedf2733147e8552ce08f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="dynamic-tracing"></a>Analisi dinamica
Funzionalità di traccia possono essere abilitati o disabilitati in qualsiasi momento di eseguire un'applicazione. In questo modo un'applicazione per tenere traccia di un numero qualsiasi di chiamate di funzione.  
  
 La variabile **ODBCSharedTraceFlag** è impostato per abilitare la traccia in modo dinamico. Questa variabile viene condiviso tra tutte le copie in esecuzione di gestione Driver. Se questa variabile viene impostata, qualsiasi applicazione è attivata per tutte le applicazioni ODBC attualmente in esecuzione. Per attivare la traccia off quando dinamica è attivata, un'applicazione chiama **SQLSetConnectAttr** su cui impostare SQL_ATTR_TRACE SQL_TRACE_OFF. Verrà visualizzata la traccia per l'applicazione solo con questa chiamata. Le applicazioni che sono collegate con Odbc32.lib è possono modificare questa variabile. Dati di traccia possono essere visualizzati in una finestra in tempo reale, anziché il file di traccia, che deve essere aperta dopo la sessione ODBC. Controlli possono essere aggiunti alla schermata di un'applicazione per attivare o disattivare la traccia in verrà.  
  
 La traccia DLL fornite con ODBC 3*x* non è thread-safe. Non è garantito che il file di log viene scritta correttamente se sono abilitata l'analisi globale (variabile **ODBCSharedTraceFlag** è impostata) e più di un'applicazione scrive nel file di traccia nello stesso momento. Questa condizione non restituisce un errore.
