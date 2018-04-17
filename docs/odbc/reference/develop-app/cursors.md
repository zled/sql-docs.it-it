---
title: Cursori | Microsoft Docs
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
- forward-only cursors [ODBC]
- scrollable cursors [ODBC]
- cursors [ODBC], about cursors
- cursors [ODBC]
- fetches [ODBC], cursors
- result sets [ODBC], fetching
- block cursors [ODBC]
ms.assetid: 0b114352-3c63-4d33-9220-182ede90e4aa
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c0c6ae5b9bda276bcd1296fcb475063fea6db204
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="cursors"></a>Cursori
Un'applicazione recupera i dati con un *cursore*. Un cursore è diverso da un set di risultati: un set di risultati è il set di righe che soddisfa i criteri di ricerca particolare, mentre un cursore è il software che restituisce le righe per l'applicazione. Il nome *cursore,* applicato ai database, probabilmente ha avuto origine il cursore in un computer terminal lampeggiante. Come tale cursore indica la posizione sullo schermo e in cui le parole tipizzate apparirà successive, un cursore su un set di risultati indica la posizione corrente nel set di risultati e la riga verrà restituita accanto.  
  
 Il modello di cursore in ODBC è basato sul modello di cursore in embedded SQL. Una differenza fondamentale tra questi modelli è che il modo di cursori viene aperti. In embedded SQL, un cursore deve essere esplicitamente dichiarato e aperti prima di poter essere utilizzato. In ODBC un cursore è aperto in modo implicito quando viene eseguita un'istruzione che crea un set di risultati. Quando il cursore è aperto, è posizionato prima della prima riga del set di risultati. In embedded SQL e ODBC è necessario chiudere un cursore dopo l'applicazione ha completato l'utilizzo.  
  
 I cursori diversi hanno caratteristiche diverse. Il tipo più comune di cursore, viene chiamato un *cursori forward-only,* può solo passare attraverso il set di risultati. Per tornare a una riga precedente, l'applicazione deve chiudere e riaprire il cursore e quindi leggere le righe dall'inizio del gruppo di risultati fino a raggiungere la riga necessaria. I cursori forward-only forniscono un meccanismo rapido per l'esecuzione di una singola iterazione di un set di risultati.  
  
 I cursori forward-only sono meno utili per le applicazioni basate su schermo, in cui l'utente scorre all'indietro e Avanti dei dati. Tali applicazioni possono utilizzare un cursore forward-only leggendo il risultato è impostato, la memorizzazione nella cache i dati in locale e l'esecuzione di scorrimento a se stessi. Tuttavia, questo funziona bene solo con piccole quantità di dati. Una soluzione migliore consiste nell'utilizzare un *con cursori scorrevoli,* che fornisce l'accesso casuale al set di risultati. Tali applicazioni possono inoltre migliorare le prestazioni mediante il recupero di più di una riga di dati contemporaneamente, con quello che viene definito un *cursore rettangolare.* Per ulteriori informazioni sui cursori a blocchi, vedere [cursori a blocchi usando](../../../odbc/reference/develop-app/using-block-cursors.md).  
  
 Il cursore forward-only è il tipo di cursore predefinito in ODBC e viene illustrato nelle sezioni seguenti. Per ulteriori informazioni sui cursori a blocchi e i cursori scorrevoli, vedere [cursori a blocchi](../../../odbc/reference/develop-app/block-cursors.md) e [cursori scorrevoli](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
> [!IMPORTANT]  
>  Eseguire il commit o il rollback di una transazione, in modo esplicito chiamando **SQLEndTran** o per operare in modalità autocommit, a causa di alcune origini dati chiudere tutti i cursori su tutte le istruzioni in una connessione. Per ulteriori informazioni, vedere gli attributi SQL_CURSOR_COMMIT_BEHAVIOR e SQL_CURSOR_ROLLBACK_BEHAVIOR il [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descrizione della funzione.
