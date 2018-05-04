---
title: SQLBindCol (libreria di cursori) | Documenti Microsoft
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
- SQLAllocStmt function [ODBC], Cursor Library
ms.assetid: f4dd546a-0a6c-4397-8ee7-fafa6b9da543
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a877b6cade18e59f12abfe807d8efa04363b3dcb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlbindcol-cursor-library"></a>SQLBindCol (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLBindCol** funzione nella libreria di cursori. Per informazioni generali su **SQLBindCol**, vedere [funzione SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md).  
  
 Un'applicazione alloca uno o più buffer per la libreria di cursori da restituire nel set di righe corrente. Chiama **SQLBindCol** una o più volte per associare i buffer per il set di risultati.  
  
 Un'applicazione può chiamare **SQLBindCol** per riassociare risultato set di colonne dopo aver chiamato **SQLExtendedFetch**, **SQLFetch**, o **SQLFetchScroll**, purché il tipo di dati C, le dimensioni di colonna e cifre decimali della colonna associata rimangono invariati. L'applicazione non è necessario chiudere il cursore per riassociare le colonne da un indirizzo diverso.  
  
 La libreria di cursori supporta l'impostazione dell'attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR per usare gli offset di associazione. (**SQLBindCol** non deve essere chiamato per la riassociazione avvenga.) Se la libreria di cursori viene utilizzata con un'applicazione ODBC 3*x* driver, l'offset di binding non è utilizzato quando **SQLFetch** viene chiamato. L'offset di binding viene usato se **SQLFetch** viene chiamato quando viene utilizzata la libreria di cursori con un'API ODBC 2. *x* driver perché **SQLFetch** viene quindi mappato a **SQLExtendedFetch**.  
  
 La libreria di cursori supporta la chiamata **SQLBindCol** per associare la colonna del segnalibro.  
  
 Quando si lavora con un ODBC 2. *x* driver, la libreria di cursori restituisce SQLSTATE HY090 (stringa di lunghezza o non valida del buffer) quando **SQLBindCol** viene chiamato per impostare la lunghezza del buffer per una colonna del segnalibro a un valore non è uguale a 4. Quando si lavora con un'applicazione ODBC 3*x* driver, la libreria di cursori consente il buffer di qualsiasi dimensione.
