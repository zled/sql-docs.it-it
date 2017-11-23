---
title: Colonne del Set di risultati di associazione | Documenti Microsoft
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
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: 4bc9c30f-83ae-4766-a746-032953c187ad
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cafac55eeca169ff83521e945f0f5e76b31f19c8
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="binding-result-set-columns"></a>Colonne del Set di risultati di associazione
Le applicazioni possono associare come molti o con il minor numero di colonne del set di risultati a propria scelta, tra cui non associazione colonne affatto. Quando viene recuperata una riga di dati, il driver restituisce i dati per le colonne associate all'applicazione. Se l'applicazione associa tutte le colonne nel set di risultati dipende dall'applicazione. Ad esempio, le applicazioni che generano i rapporti in genere hanno un formato fisso; tali applicazioni creare un set di risultati contenente tutte le colonne utilizzate nel report e quindi associare e recuperano i dati per tutte queste colonne. Le applicazioni che consentono di visualizzare schermate completa dei dati talvolta consentono all'utente di decidere le colonne da visualizzare. tali applicazioni creare un set di risultati contenente tutte le colonne, l'utente potrebbe comunque ma associare e recuperare i dati solo per le colonne selezionate dall'utente.  
  
 Dati possono essere recuperati da colonne non associate chiamando **SQLGetData**. Si tratta in genere per recuperare dati long, che spesso superano la lunghezza di un singolo buffer e devono essere recuperati in parti.  
  
 Colonne possono essere associate in qualsiasi momento, anche dopo le righe recuperate. Tuttavia, le nuove associazioni non diventano effettive fino alla successiva che viene recuperata una riga; non vengono applicate ai dati dalle righe già recuperate.  
  
 Una variabile rimane associata a una colonna fino a quando una variabile diversa è associata alla colonna, fino a quando la colonna è stata annullata chiamando **SQLBindCol** con un puntatore null come indirizzo della variabile, fino a quando tutte le colonne sono associate chiamando **SQLFreeStmt** con l'opzione SQL_UNBIND o fino a quando l'istruzione viene rilasciato. Per questo motivo, l'applicazione deve assicurarsi che tutte le variabili associate rimangono valide fino a quando sono associate. Per ulteriori informazioni, vedere [allocazione e liberando buffer](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md).  
  
 Perché le associazioni di colonna sono solo informazioni associate alla struttura dell'istruzione, possono essere impostate in qualsiasi ordine. Sono anche indipendenti del set di risultati. Si supponga, ad esempio, che un'applicazione associa le colonne del set di risultati generato dall'istruzione SQL seguente:  
  
```  
SELECT * FROM Orders  
```  
  
 Se l'applicazione esegue quindi l'istruzione SQL  
  
```  
SELECT * FROM Lines  
```  
  
 sullo stesso handle di istruzione, le associazioni di colonna per il primo set di risultati sono ancora attive perché queste sono le associazioni archiviate nella struttura di istruzione. Nella maggior parte dei casi, questo è un livello di programmazione ridotte e deve essere evitato. Al contrario, l'applicazione deve chiamare **SQLFreeStmt** con l'opzione SQL_UNBIND per separare tutte le colonne precedente e quindi associare nuovi.
