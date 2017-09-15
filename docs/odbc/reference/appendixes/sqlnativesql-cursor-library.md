---
title: SQLNativeSql (libreria di cursori) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c6062933f8f6d144b31da430788e8edd75da2eea
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLNativeSql** funzione nella libreria di cursori. Per informazioni generali su **SQLNativeSql**, vedere [funzione SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Se il driver supporta questa funzione, chiama la libreria di cursori **SQLNativeSql** nel driver e passa l'istruzione SQL. Per un aggiornamento posizionato, posizionato delete, e **selezionare per aggiornare** istruzioni, la libreria di cursori consente di modificare l'istruzione prima di passarlo al driver.  
  
> [!NOTE]  
>  La libreria di cursori restituisce erroneamente SQLSTATE 34000 (nome di cursore non valido) se il nome del cursore non è valido in un'istruzione delete che viene passato in o un aggiornamento posizionato il *InStatementText* argomento di **SQLNativeSql **. **SQLNativeSql** non è progettata per restituire gli errori di sintassi, che vengono restituiti solo dopo la preparazione o l'esecuzione.
