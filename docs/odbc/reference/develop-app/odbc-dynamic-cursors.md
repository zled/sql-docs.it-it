---
title: I cursori dinamici ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], dynamic
- dynamic cursors [ODBC]
ms.assetid: de709fd3-9eb2-44e1-a2f0-786e2b9602a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 82df10e6b8effeb040b362dcf466eb173dfce4f9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629679"
---
# <a name="odbc-dynamic-cursors"></a>Cursori dinamici ODBC
Un cursore dinamico è da considerarsi semplicemente: dinamico. È possibile rilevare eventuali modifiche apportate all'ordine, di appartenenza e i valori del set di risultati dopo l'apertura del cursore. Si supponga, ad esempio, un cursore dinamico recupera due righe e un'altra applicazione, quindi aggiorna una di queste righe ed elimina l'altro. Se il cursore dinamico tenta quindi di recupero di tali righe, non troverà la riga eliminata ma restituirà i nuovi valori per la riga aggiornata.  
  
 I cursori dinamici rilevano tutti gli aggiornamenti, eliminazione e inserimento, entrambi i propri e quelle apportate da altri utenti. (Questo è soggetta all'isolamento a livello della transazione, come impostato dall'attributo di connessione SQL_ATTR_TXN_ISOLATION). La matrice di stato di riga specificata dall'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR queste variazioni si rifletta e può contenere SQL_ROW_SUCCESS SQL_ROW_SUCCESS_WITH_INFO, SQL_ROW_ERROR, SQL_ROW_UPDATED e SQL_ROW_ADDED. Non può restituire SQL_ROW_DELETED perché un cursore dinamico non restituisce le righe eliminate all'esterno del set di righe e pertanto non li riconosce più l'esistenza dell'elemento corrispondente nella matrice di stato di riga o la riga eliminata nel set di risultati. SQL_ROW_ADDED viene restituita solo quando viene aggiornata una riga da una chiamata a **SQLSetPos**, non quando viene aggiornata da un altro cursore.  
  
 Un modo per implementare cursori dinamici del database è mediante la creazione di un indice selettivo che definisce l'appartenenza e ordinamento del risultato impostato. Poiché l'indice viene aggiornato quando altri utenti apportano modifiche, un cursore in base a tale indice è sensibile a tutte le modifiche. Selezione aggiuntivi all'interno del set di risultati definito da questo indice è possibile dall'elaborazione lungo l'indice.  
  
 È possibile simulare i cursori dinamici, richiedendo il set di risultati a ordinati in base a una chiave univoca. Con una restrizione, operazioni di recupero vengono eseguite tramite l'esecuzione di un **seleziona** istruzione ogni volta che il cursore recupera le righe. Si supponga, ad esempio, il set di risultati è definito da questa istruzione:  
  
```  
SELECT * FROM Customers ORDER BY Name, CustID  
```  
  
 Per recuperare il successivo set di righe nel set di risultati, il cursore simulato imposta i parametri di seguito **seleziona** istruzione per i valori nell'ultima riga del set di righe corrente che viene quindi eseguito:  
  
```  
SELECT * FROM Customers WHERE (Name > ?) AND (CustID > ?)  
   ORDER BY Name, CustID  
```  
  
 Questa istruzione crea un secondo set di risultati, il primo set di righe di cui è il successivo set di righe nel set di risultati originale, ovvero in questo caso, il set di righe nella tabella Customers. Il cursore restituisce questo set di righe per l'applicazione.  
  
 È interessante notare che un cursore dinamico implementato in questo modo crea effettivamente molti set di risultati, che consente di rilevare le modifiche apportate al set di risultati originale. L'applicazione mai apprende dell'esistenza di questi set di risultati ausiliario; è sufficiente, viene visualizzato come se il cursore si trova in grado di rilevare le modifiche apportate al set di risultati originale.
