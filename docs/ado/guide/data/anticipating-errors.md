---
title: Prevenzione degli errori | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- anticipating errors [ADO]
- errors [ADO], preventing
- preventing errors [ADO]
ms.assetid: ea1d4a97-58c3-476b-a496-cc80db2a90d5
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 359dc6c1bd396a0909aea36c5039a4ba5195f326
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="anticipating-errors"></a>Prevenzione degli errori
Prevenzione di errore è importante come la gestione degli errori. In questa sezione finale contiene un breve elenco di precauzioni che l'applicazione può richiedere per rendere meno probabile che si verificano errori.  
  
 Controllare lo stato degli oggetti controllando il valore **stato** proprietà prima di tentare di eseguire un'operazione utilizzando gli oggetti. Ad esempio, se l'applicazione usa globale **connessione**, controllare il **stato** proprietà per verificare se è già aperta prima di chiamare il **aprire** metodo.  
  
-   Qualsiasi programma che accetta dati da un utente deve includere il codice per convalidare i dati prima di inviarlo all'archivio dati. Non è possibile utilizzare l'archivio dati, il provider, ADO o anche il linguaggio di programmazione per la notifica dei problemi. È necessario controllare ogni byte immesso dagli utenti, assicurandosi che i dati siano del tipo corretto per il campo e che i campi obbligatori non sono vuoti.  
  
 Controllare i dati prima di provare a scrivere i dati nell'archivio dati. È il modo più semplice per eseguire questa operazione per gestire il **WillMove** evento o **WillUpdateRecordset** evento. Per una descrizione più completa di gestione degli eventi di ADO, vedere [gestione di eventi ADO](../../../ado/guide/data/handling-ado-events.md).  
  
 Assicurarsi che **Recordset** oggetti non sono presenti oltre i limiti del **Recordset** prima di provare a spostare il puntatore del record. Se si tenta di **MoveNext** quando **EOF** è True o **MovePrev** quando **BOF** è True, verrà generato un errore. Se si esegue una del **spostare** metodi quando entrambi **EOF** e **BOF** sono True, verrà generato un errore.  
  
 Errori si verificano anche quando si tenta di eseguire operazioni quali **Seek** e **trovare** su un oggetto vuoto **Recordset**.

