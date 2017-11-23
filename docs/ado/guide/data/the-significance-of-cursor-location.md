---
title: Il significato della posizione del cursore | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- server-side cursors [ADO]
- cursors [ADO], client-side
- client-side cursors [ADO]
- cursors [ADO], server-side
ms.assetid: 70ef5b1c-0459-41a1-b796-031f61a29a8a
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 541b0195abbe4a37c3a2090add0b0cf5dbbeb568
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="the-significance-of-cursor-location"></a>Il significato della posizione del cursore
Ogni cursore utilizza risorse temporanee per la memorizzazione dei dati. Queste risorse possono essere memoria, un file di paging su disco, i file su disco temporaneo o un archivio temporaneo nel database. Il cursore viene chiamato un *sul lato client* cursore quando queste risorse si trovano nel computer client. Il cursore viene chiamato un *sul lato server* cursore quando queste risorse si trovano nel server.  
  
## <a name="client-side-cursors"></a>Cursori sul lato client  
 In ADO chiamare per un cursore sul lato client utilizzando il **adUseClient CursorLocationEnum.** Con un cursore sul lato client non keyset, il server invia l'intero set di risultati in rete come computer client. Il client fornisce e gestisce le risorse temporanee necessarie dal set di risultati e cursore. L'applicazione sul lato client possibile sfogliare l'intero set per determinare quali righe richiede di risultati.  
  
 Cursori statici o basati su keyset sul lato client possono avere un carico significativo nella workstation se includono troppe righe. Anche se tutte le librerie di cursore sono in grado di generare i cursori con migliaia di righe, le applicazioni progettate per recuperare tali set di righe di grandi dimensioni potrebbero essere scarse. Esistono eccezioni, ovviamente. Per alcune applicazioni, un cursore sul lato client di grandi dimensioni potrebbe essere perfettamente appropriato e le prestazioni potrebbero non essere un problema.  
  
 Un vantaggio evidente del cursore sul lato client è una risposta rapida. Dopo aver scaricato il set di risultati al computer client, l'esplorazione tramite le righe è molto veloce. L'applicazione è in genere più scalabile con cursori sul lato client perché i requisiti di risorse del cursore vengono inseriti in ogni client separata e non nel server.  
  
## <a name="server-side-cursors"></a>Cursori sul lato server  
 In ADO chiamare per un cursore sul lato server utilizzando il **adUseServer CursorLocationEnum.** Con un cursore sul lato server, il server gestisce il set di risultati utilizzando le risorse fornite dal computer del server. Il cursore sul lato server restituisce solo i dati richiesti in rete. Questo tipo di cursore può talvolta fornisca prestazioni migliori rispetto il cursore sul lato client, specialmente in situazioni in cui un eccessivo traffico di rete è un problema.  
  
 Tuttavia, è importante sottolineare che un cursore sul lato server è, almeno temporaneamente: utilizzo delle risorse del server per ogni client attivo. È necessario pianificare di conseguenza per assicurarsi che l'hardware del server sia in grado di gestire tutti i cursori sul lato server richiesti dai client attivi. Inoltre un cursore sul lato server può essere lento, perché fornisce solo l'accesso a riga singola, non è disponibile alcun cursore batch.  
  
 I cursori sul lato server sono utili durante l'inserimento, aggiornamento o eliminazione di record. Con cursori sul lato server, è possibile disporre più istruzioni attive nella stessa connessione.
