---
title: I cursori dinamici ODBC | Documenti Microsoft
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
helpviewer_keywords:
- cursors [ODBC], dynamic
- dynamic cursors [ODBC]
ms.assetid: de709fd3-9eb2-44e1-a2f0-786e2b9602a6
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e0d82da741babc168ce305ed8134d8f44f682f57
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-dynamic-cursors"></a>Cursori dinamici ODBC
Un cursore dinamico è esattamente questo: dinamica. È possibile rilevare eventuali modifiche apportate ai valori del set di risultati dopo l'apertura del cursore, ordine e l'appartenenza. Si supponga, ad esempio, un cursore dinamico vengono recuperate due righe e un'altra applicazione, quindi aggiorna una di queste righe ed elimina l'altro. Se il cursore dinamico tenta quindi di recupero di tali righe, non troverà la riga eliminata, ma restituirà i nuovi valori per la riga aggiornata.  
  
 I cursori dinamici rilevano tutti gli aggiornamenti, Elimina e inserisce, entrambi i propri e quelle apportate da altri utenti. (Questo è soggetto all'isolamento livello della transazione, come impostato dall'attributo di connessione SQL_ATTR_TXN_ISOLATION). La matrice di stato di riga specificata dall'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR riflette le modifiche e può contenere SQL_ROW_SUCCESS, SQL_ROW_SUCCESS_WITH_INFO, SQL_ROW_ERROR, SQL_ROW_UPDATED e SQL_ROW_ADDED. Non può restituire SQL_ROW_DELETED perché un cursore dinamico non restituisce le righe eliminate all'esterno del set di righe e pertanto non riconosce l'esistenza di una riga eliminata nel set di risultati o il relativo elemento corrispondente nella matrice di stato di riga. SQL_ROW_ADDED viene restituito solo quando viene aggiornata una riga da una chiamata a **SQLSetPos**, non quando viene aggiornato da un altro cursore.  
  
 Un modo per implementare cursori dinamici nel database mediante la creazione di un indice selettivo che definisce l'appartenenza e l'ordinamento del risultato è. Poiché l'indice viene aggiornato quando altri utenti di apportare modifiche, un cursore in base a tale indice è attiva per tutte le modifiche. Selezione aggiuntivi all'interno del set di risultati definito per questo indice è possibile dall'elaborazione lungo l'indice.  
  
 I cursori dinamici possono essere simulati richiedendo il set di risultati per essere ordinati in base a una chiave univoca. Con una restrizione, operazioni di recupero vengono eseguite tramite l'esecuzione di un **selezionare** istruzione ogni volta che il cursore recupera le righe. Si supponga, ad esempio, il set di risultati è definito da questa istruzione:  
  
```  
SELECT * FROM Customers ORDER BY Name, CustID  
```  
  
 Per recuperare il successivo set di righe nel set di risultati, il cursore simulato imposta i parametri nell'esempio seguente **selezionare** istruzione ai valori nell'ultima riga del set di righe corrente e quindi esegue:  
  
```  
SELECT * FROM Customers WHERE (Name > ?) AND (CustID > ?)  
   ORDER BY Name, CustID  
```  
  
 Questa istruzione consente di creare un secondo set di risultati, il primo set di righe di cui è il successivo set di righe nel set di risultati originale: in questo caso, il set di righe nella tabella Customers. Il cursore restituisce questo set di righe per l'applicazione.  
  
 È interessante notare che un cursore dinamico implementato in questo modo crea effettivamente molti set di risultati, che consente di rilevare le modifiche apportate al set di risultati originale. Mai l'applicazione viene a conoscenza dell'esistenza di questi set di risultati ausiliario; è sufficiente, viene visualizzato come se il cursore è in grado di rilevare le modifiche apportate al set di risultati originale.
