---
title: Determinazione delle funzionalità del cursore | Documenti Microsoft
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
- scrollable cursors [ODBC]
- cursors [ODBC], capabilities
- cursors [ODBC], scrollable
ms.assetid: 35be486c-8f2d-4cec-beb8-df14151abfef
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3974fb30a9151cdcf681a106ddcf3073b63f66b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="determining-cursor-capabilities"></a>Determinazione delle funzionalità del cursore
Le quattro opzioni seguenti in **SQLGetInfo** vengono descritti i tipi di cursori supportati e quali sono le relative funzionalità:  
  
-   SQL_CURSOR_SENSITIVITY. Indica se un cursore è sensibile alle modifiche apportate da un altro cursore.  
  
-   SQL_SCROLL_OPTIONS. Elenca i tipi di cursore supportati (forward-only, statici, basati su keyset, dinamici o misti). Tutte le origini dati devono supportare i cursori forward-only.  
  
-   SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 o SQL_STATIC_CURSOR_ATTRIBUTES1 (a seconda del tipo di cursore). Elenca i tipi di istruzione fetch supportati dai cursori scorrevoli. I bit nel valore restituito corrispondono ai tipi di istruzione fetch in **SQLFetchScroll**.  
  
-   SQL_KEYSET_CURSOR_ATTRIBUTES2 o SQL_STATIC_CURSOR_ATTRIBUTES2 (a seconda del tipo di cursore). Vengono elencati i cursori statici e basati su keyset rilevano i propri aggiornamenti, eliminazioni e inserimenti.  
  
 Un'applicazione può determinare funzionalità del cursore in fase di esecuzione chiamando **SQLGetInfo** con queste opzioni. Viene eseguita in genere da applicazioni generiche. Funzionalità del cursore può essere determinata anche durante lo sviluppo di applicazioni e il relativo utilizzo hardcoded nell'applicazione. Viene eseguita in genere da applicazioni personalizzate e verticale, ma può essere eseguita anche dalle applicazioni generiche che usano un'implementazione di cursore sul lato client, ad esempio la libreria di cursori ODBC.
