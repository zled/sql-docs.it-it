---
title: Caratteristiche del cursore e tipo di cursore | Documenti Microsoft
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
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: 6f67edd2-ae71-4ca0-9b2d-abf4c20dc17b
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 45a3003ac39e806dbd012b79b974160f3530fc32
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="cursor-characteristics-and-cursor-type"></a>Caratteristiche del cursore e tipo di cursore
Un'applicazione può specificare le caratteristiche di un cursore anziché specificare il tipo di cursore (forward-only, statico, basati su keyset o dinamico). A tale scopo, l'applicazione seleziona scorrimento del cursore (impostando l'attributo di istruzione SQL_ATTR_CURSOR_SCROLLABLE) e sensibilità (impostando l'attributo di istruzione SQL_ATTR_CURSOR_SENSITIVITY) prima di aprire il cursore sull'istruzione handle. Il driver quindi sceglie il tipo di cursore che fornisce in modo più efficiente le caratteristiche che l'applicazione richiesta.  
  
 Ogni volta che un'applicazione imposta uno degli attributi di istruzione SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY o SQL_ATTR_CURSOR_TYPE, il driver apporta qualsiasi modifica necessaria per gli altri attributi di istruzione in questo set di quattro attributi in modo che i relativi valori rimangono coerenti. Di conseguenza, quando l'applicazione specifica di una caratteristica di cursore, il driver può modificare l'attributo che indica il tipo di cursore in base a questa selezione implicita; Quando l'applicazione specifica un tipo, il driver può modificare uno degli altri attributi siano coerenti con le caratteristiche del tipo selezionato. Per ulteriori informazioni su questi attributi di istruzione, vedere il [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) descrizione della funzione.  
  
 Il rischio di ottenere un cursore che non è il metodo più efficiente disponibile in tale driver di soddisfare i requisiti dell'applicazione viene eseguita un'applicazione che imposta gli attributi di istruzione per specificare un tipo di cursore e delle caratteristiche del cursore.  
  
 L'impostazione implicita di attributi di istruzione è definito dal driver con la differenza che deve seguire queste regole:  
  
-   I cursori forward-only non sono mai supporta lo scorrimento. visualizzare la definizione della SQL_ATTR_CURSOR_SCROLLABLE in [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
-   Senza distinzione di cursori non sono mai aggiornabili (e pertanto la concorrenza è di sola lettura); si basa sulla loro definizione dei cursori distinzione in standard ISO SQL.  
  
 Di conseguenza, l'impostazione implicita di attributi di istruzione si verifica nei casi descritti nella tabella seguente.  
  
|Applicazione imposta attributi|Altri attributi impostati in modo implicito|  
|-----------------------------------|-------------------------------------|  
|SQL_ATTR_CONCURRENCY per SQL_CONCUR_READ_ONLY|SQL_ATTR_CURSOR_SENSITIVITY su SQL_INSENSITIVE.|  
|SQL_ATTR_CONCURRENCY per SQL_CONCUR_LOCK o SQL_CONCUR_ROWVER, SQL_CONCUR_VALUES|SQL_ATTR_CURSOR_SENSITIVITY SQL_UNSPECIFIED o SQL_SENSITIVE, come definito dal driver. Non si può mai essere impostato su SQL_INSENSITIVE, perché distinzione sono sempre di sola lettura.|  
|SQL_ATTR_CURSOR_SCROLLABLE su SQL_NONSCROLLABLE|SQL_ATTR_CURSOR_TYPE per SQL_CURSOR_FORWARD_ONLY|  
|SQL_ATTR_CURSOR_SCROLLABLE su SQL_SCROLLABLE|SQL_ATTR_CURSOR_TYPE SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN o SQL_CURSOR_DYNAMIC, come specificato dal driver. Non si è mai SQL_CURSOR_FORWARD_ONLY.|  
|SQL_ATTR_CURSOR_SENSITIVITY su SQL_INSENSITIVE|SQL_ATTR_CONCURRENCY per SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE per SQL_CURSOR_STATIC.|  
|SQL_ATTR_CURSOR_SENSITIVITY su SQL_SENSITIVE|SQL_ATTR_CONCURRENCY per SQL_CONCUR_LOCK o SQL_CONCUR_ROWVER, SQL_CONCUR_VALUES, come specificato dal driver. Non si è mai impostato su SQL_CONCUR_READ_ONLY.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN o SQL_CURSOR_DYNAMIC, come specificato dal driver.|  
|SQL_ATTR_CURSOR_SENSITIVITY per SQL_UNSPECIFIED|SQL_ATTR_CONCURRENCY su SQL_CONCUR_READ_ONLY, SQL_CONCUR_LOCK, SQL_CONCUR_ROWVER o SQL_CONCUR_VALUES, come specificato dal driver.<br /><br /> SQL_ATTR_CURSOR_TYPE SQL_CURSOR_FORWARD_ONLY, SQL_CURSOR_STATIC, SQL_CURSOR_KEYSET_DRIVEN o SQL_CURSOR_DYNAMIC, come specificato dal driver.|  
|SQL_ATTR_CURSOR_TYPE per SQL_CURSOR_DYNAMIC|SQL_ATTR_SCROLLABLE su SQL_SCROLLABLE.<br /><br /> SQL_ATTR_CURSOR_SENSITIVITY su SQL_SENSITIVE. (Ma solo se non è uguale a SQL_CONCUR_READ_ONLY SQL_ATTR_CONCURRENCY. I cursori dinamici aggiornabili sono sempre sensibili alle modifiche apportate nella propria transazione.)|  
|SQL_ATTR_CURSOR_TYPE per SQL_CURSOR_FORWARD_ONLY|SQL_ATTR_CURSOR_SCROLLABLE su SQL_NONSCROLLABLE.|  
|SQL_ATTR_CURSOR_TYPE per SQL_CURSOR_KEYSET_DRIVEN|SQL_ATTR_SCROLLABLE su SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED o SQL_SENSITIVE (criteri definito dal driver, se SQL_ATTR_CONCURRENCY non SQL_CONCUR_READ_ONLY).|  
|SQL_ATTR_CURSOR_TYPE per SQL_CURSOR_STATIC|SQL_ATTR_SCROLLABLE su SQL_SCROLLABLE.<br /><br /> SQL_ATTR_SENSITIVITY su SQL_INSENSITIVE (se SQL_ATTR_CONCURRENCY SQL_CONCUR_READ_ONLY).<br /><br /> SQL_ATTR_SENSITIVITY SQL_UNSPECIFIED o SQL_SENSITIVE (se non SQL_ATTR_CONCURRENCY è SQL_CONCUR_READ_ONLY).|
