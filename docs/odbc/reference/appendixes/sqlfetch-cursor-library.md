---
title: SQLFetch (libreria di cursori) | Documenti Microsoft
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
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d0ba4112900a3d89e74582e3bf3549b196ba2ab
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLFetch** funzione nella libreria di cursori. Per informazioni generali su **SQLFetch**, vedere [SQLFetch-funzione](../../../odbc/reference/syntax/sqlfetch-function.md).  
  
 Quando si utilizza la libreria di cursori, le chiamate a **SQLFetch** ReadContentAsBinHex con chiamate a **SQLFetchScroll** o **SQLExtendedFetch**.  
  
 Se **SQLFetch** viene chiamato con SQL_ATTR_ROW_ARRAY_SIZE impostata su un valore maggiore di 1, la libreria di cursori passerà la chiamata al driver. Se il driver è un'API ODBC 2. *x* driver, le dimensioni del set di righe verranno ignorata e la chiamata a **SQLFetch** restituirà una singola riga di dati.  
  
 Se la libreria di cursori viene usata con un ODBC 2. *x* driver, un binding offset (come definito dall'attributo di istruzione SQL_ATTR_ROW_BIND_OFFSET_PTR) non è utilizzato quando **SQLFetch** viene chiamato.  
  
 Quando viene caricata la libreria di cursori, un'applicazione non è possibile chiamare **SQLFetch** per recuperare colonne segnalibro. La libreria di cursori passa la chiamata a **SQLFetch** tramite il driver, ma la funzione le chiamate per abilitare i segnalibri e associare la colonna del segnalibro vengono intercettate dalla libreria di cursori.
