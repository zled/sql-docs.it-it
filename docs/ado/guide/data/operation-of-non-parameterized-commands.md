---
title: Funzionamento dei comandi senza parametri | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- non-parameterized commands [ADO]
- data shaping [ADO], non-parameterized commands
ms.assetid: 9700e50a-9f17-4ba3-8afb-f750741dc6ca
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8aa3ed637aa9206921f6da91f0218f67faf0154a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35272280"
---
# <a name="operation-of-non-parameterized-commands"></a>Funzionamento dei comandi senza parametri
Per i comandi senza parametri, vengono eseguiti tutti i comandi del provider e **recordset** vengono creati durante l'esecuzione del comando. Se il comando viene eseguito in modo sincrono, tutti i **recordset** verrà popolato completamente. Se è stata selezionata una modalità di popolamento asincrono, lo stato di popolamento del **recordset** dipendono dalla modalità di popolamento e la dimensione del **recordset**.  
  
 Ad esempio, il *comando padre* potrebbe restituire un **Recordset** dei clienti per una società da una tabella Customers e *comando figlio* potrebbe restituire un **Recordset** di ordini per tutti i clienti di una tabella Orders.  
  
```  
SHAPE {SELECT * FROM Customers}   
   APPEND ({SELECT * FROM Orders} AS chapOrders   
   RELATE customerID TO customerID)  
```  
  
 Per le relazioni padre-figlio senza parametri, ogni elemento padre e figlio **Recordset** oggetto deve contenere una colonna in comune per associarli. Le colonne sono denominate nella clausola RELATE *colonna padre* prima e quindi *colonna figlio*. Le colonne possono avere nomi diversi nei rispettivi **Recordset** oggetti ma deve fare riferimento alle stesse informazioni per specificare una relazione significativa. Ad esempio, il **clienti** e **Recordset ordini** oggetti potrebbe avere un campo customerID. Poiché l'appartenenza dell'oggetto figlio **Recordset** è determinato dal comando del provider, l'elemento figlio **Recordset** può contenere righe orfane. Queste righe orfane sono inaccessibili senza modificare la forma aggiuntive.  
  
 Il data shaping accoda una colonna a capitoli all'oggetto padre **Recordset**. I valori nella colonna del capitolo sono riferimenti alle righe figlio **Recordset**, che soddisfa la clausola RELATE. Lo stesso valore è nel *colonna padre* di una riga padre specificato perché è nel *colonna figlio* di tutte le righe dell'elemento figlio capitolo. Quando più clausole TO vengono utilizzate nella stessa clausola RELATE, essi vengono combinate in modo implicito utilizzando l'operatore AND. Se le colonne padre nella clausola RELATE non costituiscono una chiave per l'elemento padre **Recordset**, una riga di singolo elemento figlio può avere più righe padre.  
  
 Quando si accede al riferimento nella colonna del capitolo, ADO recupera automaticamente la **Recordset** rappresentato dal riferimento. Si noti che in un comando senza parametri, sebbene l'intero figlio **Recordset** è stato recuperato, il capitolo include solo un subset di righe.  
  
 Se non include la colonna accodata *alias capitolo*, verrà generato un nome per tale automaticamente. A [campo](../../../ado/reference/ado-api/field-object.md) la colonna verrà aggiunta al relativo oggetto di **Recordset** dell'oggetto [campi](../../../ado/reference/ado-api/fields-collection-ado.md) insieme e il relativo tipo di dati sarà **adChapter**.  
  
 Per informazioni sullo spostamento gerarchico **Recordset**, vedere [accesso alle righe in un Recordset gerarchico](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Data Shaping di esempio](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale forma](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)
