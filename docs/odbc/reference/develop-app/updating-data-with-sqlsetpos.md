---
title: Aggiornamento dei dati con SQLSetPos | Documenti Microsoft
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
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating data
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a25d331649510f7e2d407842dc915df2da7d6184
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updating-data-with-sqlsetpos"></a>Aggiornamento dei dati con SQLSetPos
Le applicazioni possono aggiornare o eliminare qualsiasi riga nel set di righe con **SQLSetPos**. La chiamata **SQLSetPos** rappresenta un'alternativa utile alla creazione ed esecuzione di un'istruzione SQL. Consente un driver ODBC supporta gli aggiornamenti posizionati anche quando l'origine dati non supporta le istruzioni SQL posizionate. È parte del paradigma di ottenere accesso completo del database tramite le chiamate di funzione.  
  
 **SQLSetPos** opera su set di righe corrente e può essere usata solo dopo una chiamata a **SQLFetchScroll**. L'applicazione specifica il numero della riga da aggiornare, eliminare o inserire e vengono recuperati i nuovi dati per la riga dal buffer di set di righe. **SQLSetPos** può essere utilizzato anche per designare una riga specificata come riga corrente o per aggiornare una particolare riga nel set di righe dall'origine dati.  
  
 Dimensioni del set di righe sono impostata da una chiamata a **SQLSetStmtAttr** con un *attributo* argomento di SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** utilizza nuove dimensioni del set di righe, tuttavia, solo dopo una chiamata a **SQLFetch** o **SQLFetchScroll**. Se le dimensioni del set di righe viene modificata, ad esempio **SQLSetPos** viene chiamato e quindi **SQLFetch** o **SQLFetchScroll** viene chiamato e la chiamata a **SQLSetPos** utilizza le dimensioni del set di righe precedenti durante **SQLFetch** o **SQLFetchScroll** utilizza le nuove dimensioni del set di righe.  
  
 La prima riga nel set di righe è il numero di riga 1. Il *RowNumber* argomento in **SQLSetPos** deve identificare una riga nel set di righe, ovvero il valore deve essere compreso nell'intervallo compreso tra 1 e il numero di righe recuperate più di recente (che può essere minore di dimensione del set di righe). Se *RowNumber* è 0, l'operazione si applica a tutte le righe nel set di righe.  
  
 Poiché la maggior parte delle interazioni con i database relazionali vengono eseguite tramite SQL, **SQLSetPos** è ampiamente supportato. Tuttavia, un driver può facilmente emulare creazione ed esecuzione di un **aggiornamento** o **eliminare** istruzione.  
  
 Per determinare quali operazioni **SQLSetPos** supporta, un'applicazione chiama **SQLGetInfo** con SQL_DYNAMIC_CURSOR_ATTRIBUTES1 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ Oggetti ATTRIBUTES1, o l'opzione relativa alle informazioni SQL_STATIC_CURSOR_ATTRIBUTES1 (a seconda del tipo di cursore).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Aggiornamento delle righe nel set di righe con SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Eliminazione di righe nel set di righe con SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
