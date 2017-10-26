---
title: Limitazioni dell'utilizzo di cursori | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 54581e6bf4aceebc50a752ee460458671e8047bd
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Limitazioni dell'utilizzo di cursori
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 È necessario essere in grado di recuperare una singola colonna ROWID per la tabella query. Impossibile utilizzare un cursore gestito da keyset in join, query o istruzioni che contengono una parola chiave DISTINCT, GROUP BY, UNION, INTERSECT o meno le clausole.  
  
 Inoltre, se l'applicazione utilizza gli alias di tabella, basati su keyset non è attivo. sono necessari tipi di cursore forward-only o statico. Il keyset utilizzando il tipo di cursore con gli alias di tabella causerà l'errore seguente: "[Microsoft] [driver ODBC per Oracle] non è possibile utilizzare cursori basati su Keyset in join, con l'operatore union, intersect o set di risultati meno o in sola lettura."  
  
> [!NOTE]  
>  A causa del modo il driver gestisce l'istruzione SQL che viene inviato al server Oracle, Oracle restituisce internamente il messaggio di errore seguente: "ORA 00964: tabella nome non in elenco."

