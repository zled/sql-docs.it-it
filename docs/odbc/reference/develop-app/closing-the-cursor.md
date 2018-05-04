---
title: Chiusura del cursore | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], closing
- closing cursors [ODBC]
ms.assetid: 4f19bf5e-6d8c-40ae-a975-cfd62a0790ec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 794180396f9b233d32283f46264a696c80559d21
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="closing-the-cursor"></a>Chiusura del cursore
Quando un'applicazione ha terminato di utilizzare un cursore, chiama **SQLCloseCursor** per chiudere il cursore. Esempio:  
  
```  
SQLCloseCursor(hstmt);  
```  
  
 E la chiusura del cursore, non utilizzare l'istruzione in cui il cursore è aperto per la maggior parte delle altre operazioni, ad esempio l'esecuzione di un'altra istruzione SQL. Per un elenco completo delle funzioni che può essere chiamato mentre è aperto un cursore, vedere [tabelle di transizione dello stato di appendice b: ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
> [!NOTE]  
>  Per chiudere un cursore, un'applicazione deve chiamare **SQLCloseCursor**, non **SQLCancel**.  
  
 I cursori rimangono aperti fino a quando non sono chiuse in modo esplicito, tranne quando una transazione è stato eseguito il commit o rollback, nel qual caso alcune origini dati chiudere il cursore. In particolare, il raggiungimento della fine del risultato impostato, quando **SQLFetch** restituisce SQL_NO_DATA, non si chiude un cursore. Anche i cursori nel set di risultati vuoti (set di risultati creati quando un'istruzione è stata eseguita correttamente, ma che non ha restituito righe) devono essere chiuso in modo esplicito.
