---
title: SQLEndTran (libreria di cursori) | Documenti Microsoft
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
- SQLEndTran function [ODBC], Cursor Library
ms.assetid: 92340b87-9084-4838-a509-e9ca22d5fd5c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fe61f62906c113d7ea07c96f20f816456c6bfb1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32907416"
---
# <a name="sqlendtran-cursor-library"></a>SQLEndTran (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLEndTran** funzione nella libreria di cursori. Per informazioni generali su **SQLEndTran**, vedere [funzione SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
 La libreria di cursori non supporta le transazioni e passa le chiamate a **SQLEndTran** direttamente al driver. Tuttavia, la libreria di cursori supporta la funzionalità di commit e rollback del cursore restituito dall'origine dati con i tipi di informazioni SQL_CURSOR_ROLLBACK_BEHAVIOR e SQL_CURSOR_COMMIT_BEHAVIOR:  
  
-   Per origini dati per conservare i cursori nelle transazioni, rollback delle modifiche che viene eseguito il rollback dell'origine dati non in cache della libreria di cursori. Per rendere la cache corrispondono ai dati nell'origine dati, l'applicazione deve chiudere e riaprire il cursore.  
  
-   Per origini dati per chiudere i cursori in base ai limiti delle transazioni, la libreria di cursori chiude i cursori ed elimina la cache per tutte le istruzioni per la connessione.  
  
-   Per origini dati per eliminare le istruzioni preparate in base ai limiti delle transazioni, l'applicazione deve reprepare tutte le istruzioni preparate per la connessione prima di rieseguire li.
