---
title: SQLSetScrollOptions (libreria di cursori) | Documenti Microsoft
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
- SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 96041fdfcf9dbad53513f402faad8b2aeaf37cf3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLSetScrollOptions** funzione nella libreria di cursori. Per informazioni generali su **SQLSetScrollOptions**, vedere [SQLSetScrollOptions funzione](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md).  
  
 La libreria di cursori supporta **SQLSetScrollOptions** solo per compatibilità con le versioni precedenti; le applicazioni devono utilizzare invece gli attributi di istruzione SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE e SQL_ATTR_ROW_ARRAY_SIZE.
