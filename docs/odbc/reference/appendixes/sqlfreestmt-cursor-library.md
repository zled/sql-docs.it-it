---
title: SQLFreeStmt (libreria di cursori) | Documenti Microsoft
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
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8b7eea7d0a956543ba765dc7c15cf48102efa9e4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLFreeStmt** funzione nella libreria di cursori. Per informazioni generali su **SQLFreeStmt**, vedere [SQLFreeStmt-funzione](../../../odbc/reference/syntax/sqlfreestmt-function.md).  
  
 Se un'applicazione chiama **SQLFreeStmt** con l'opzione SQL_UNBIND dopo aver chiamato **SQLExtendedFetch**, **SQLFetch**, o **SQLFetchScroll**, la libreria di cursori restituisce un errore. Prima di è possibile separare le colonne del set di risultati, un'applicazione deve chiamare **SQLCloseCursor** o **SQLFreeStmt** con l'opzione di SQL_CLOSE.
