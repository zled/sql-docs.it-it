---
title: Che cos'è un blocco? | Microsoft Docs
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], locking
- locks [ADO], about locking
ms.assetid: f8989555-28c6-4c17-9bf8-7f44a8a5c407
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c28c8b420b6ed8662d503c55594a85ef8d2c98ef
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="what-is-a-lock"></a>Che cos'è un blocco?
Il blocco è il processo mediante il quale un DBMS limita l'accesso a una riga in un ambiente multiutente. Quando una riga o colonna è bloccata in modo esclusivo, altri utenti non sono consentiti per accedere ai dati bloccati finché il blocco viene rilasciato. In questo modo si garantisce che due utenti non è possibile aggiornare contemporaneamente la stessa colonna in una riga.  
  
 Blocchi possono risultare molto costosi da una prospettiva della risorsa e devono essere utilizzati solo quando necessario per mantenere l'integrità dei dati. In un database in cui è Impossibile cercare centinaia o migliaia di utenti di accedere a un record di ogni secondo, ad esempio un database connesso a Internet, ovvero numero eccessivo di blocchi potrebbe compromettere rapidamente le prestazioni dell'applicazione.  
  
 È possibile controllare come l'origine dati e la libreria di cursori di ADO gestire la concorrenza, scegliendo l'opzione di blocco appropriato.  
  
 Impostare il **LockType** proprietà prima di aprire un **Recordset** per specificare il tipo di blocco che il provider deve utilizzare durante l'apertura del file. Leggere la proprietà per restituire il tipo di blocco in uso su un oggetto aperto **Recordset** oggetto.  
  
 I provider potrebbero non supportare tutti i tipi di blocco. Se un provider non supporta la richiesta **LockType** impostazione sostituirà un altro tipo di blocco. Per determinare la funzionalità di blocco disponibile in un **Recordset** oggetto, usare il [supporta](../../../ado/reference/ado-api/supports-method.md) metodo con **valori adUpdate** e **adUpdateBatch**.  
  
 Il **adLockPessimistic** impostazione non è supportata se il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) è impostata su **adUseClient.** Se è impostato un valore non supportato, verrà restituito alcun errore; è supportato il più vicino **LockType** verrà utilizzato.  
  
 Il **LockType** proprietà è di lettura/scrittura quando il **Recordset** è chiuso e di sola lettura quando è aperto.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Tipi di blocchi](../../../ado/guide/data/types-of-locks.md)
