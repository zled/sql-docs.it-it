---
title: SQLCloseCursor_ODBC | Documenti Microsoft
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
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6477530573cc6fccd173e1cb1fbed7c59141a4e0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLCloseCursor** funzione nella libreria di cursori. Per informazioni generali su **SQLCloseCursor**, vedere [funzione SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 La libreria di cursori non supporta la chiamata **SQLCloseCursor** senza un cursore aperto. Questo tentativo restituisce SQLSTATE 24000 (stato del cursore non valido). La chiamata **SQLFreeStmt** con un *opzione* di SQL_CLOSE quando nessun cursore è aperto è supportato dalla libreria di cursori.
