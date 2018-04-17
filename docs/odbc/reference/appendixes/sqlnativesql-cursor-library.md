---
title: SQLNativeSql (libreria di cursori) | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f9ce0357981dbc7a499bf0dc0cefc52313a2596a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLNativeSql** funzione nella libreria di cursori. Per informazioni generali su **SQLNativeSql**, vedere [funzione SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md).  
  
 Se il driver supporta questa funzione, chiama la libreria di cursori **SQLNativeSql** nel driver e passa l'istruzione SQL. Per un aggiornamento posizionato, posizionato delete, e **selezionare per aggiornare** istruzioni, la libreria di cursori consente di modificare l'istruzione prima di passarlo al driver.  
  
> [!NOTE]  
>  La libreria di cursori restituisce erroneamente SQLSTATE 34000 (nome di cursore non valido) se il nome del cursore non è valido in un'istruzione delete che viene passato in o un aggiornamento posizionato il *InStatementText* argomento di **SQLNativeSql** . **SQLNativeSql** non è progettata per restituire gli errori di sintassi, che vengono restituiti solo al momento di preparazione dell'istruzione o l'esecuzione.
