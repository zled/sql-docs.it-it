---
title: "Modalità batch | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ADO], batch mode
- batch mode [ADO]
- updating data [ADO], batch mode
ms.assetid: 0cb548e0-fcb4-4c49-98c8-be287911f826
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 92e249a7c2d5b0c01e291f4829d5c4f8c580fb2c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="batch-mode"></a>Modalità batch
Attiva la modalità batch quando il **LockType** è impostata su **adLockBatchOptimistic** e l'aggiornamento in batch è supportato dal provider. Alcune impostazioni del tipo di blocco non sono disponibili a seconda della posizione del cursore. Ad esempio, un tipo di blocco pessimistico non è disponibile quando il **CursorLocation** è impostato su **adUseClient**. Al contrario, un provider non supporta un blocco ottimistico batch quando il cursore si trova nel server. È consigliabile utilizzare l'aggiornamento in blocco con un solo cursore statico o keyset.  
  
 Il **UpdateBatch** metodo viene utilizzato per inviare **Recordset** modifiche memorizzate nel buffer di copia al server per aggiornare l'origine dati. Nella sezione seguente, verrà aperta una **Recordset** in modalità batch, apportare modifiche al buffer di copia e quindi inviare le modifiche all'origine dati tramite una chiamata a **UpdateBatch**.  
  
 Questa sezione contiene i seguenti argomenti:  
  
-   [Invio di aggiornamenti: metodo UpdateBatch](../../../ado/guide/data/sending-the-updates-updatebatch-method.md)  
  
-   [Il filtro per i record aggiornati](../../../ado/guide/data/filtering-for-updated-records.md)  
  
-   [Gestione degli aggiornamenti non riusciti](../../../ado/guide/data/dealing-with-failed-updates.md)  
  
-   [Rilevamento e risoluzione dei conflitti](../../../ado/guide/data/detecting-and-resolving-conflicts.md)  
  
-   [Disconnessione e riconnessione dell'oggetto Recordset](../../../ado/guide/data/disconnecting-and-reconnecting-the-recordset.md)  
  
-   [Aggiornamento unita risultati: Tabella univoca](../../../ado/guide/data/updating-joined-results-unique-table.md)

