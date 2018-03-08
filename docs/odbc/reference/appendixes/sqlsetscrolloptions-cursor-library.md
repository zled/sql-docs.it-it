---
title: SQLSetScrollOptions (libreria di cursori) | Documenti Microsoft
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
helpviewer_keywords: SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e4b8d28541eda6afea8d72c442922f79b5160a62
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLSetScrollOptions** funzione nella libreria di cursori. Per informazioni generali su **SQLSetScrollOptions**, vedere [SQLSetScrollOptions funzione](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 La libreria di cursori supporta **SQLSetScrollOptions** solo per compatibilità con le versioni precedenti; le applicazioni devono utilizzare invece gli attributi di istruzione SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE e SQL_ATTR_ROW_ARRAY_SIZE.
