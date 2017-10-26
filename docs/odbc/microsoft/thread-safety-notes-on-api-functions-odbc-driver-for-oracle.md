---
title: Thread Safety note sulle funzioni API (Driver ODBC per Oracle) | Documenti Microsoft
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
- ODBC driver for Oracle [ODBC], threading
- threading options [ODBC]
- multiple concurrent statements [ODBC]
ms.assetid: f0c9bdfd-f79d-4088-9ecb-afcd8ca7fb73
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cc4a28976342768f5c7b2d1cfe8a1d3be6544306
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="thread-safety-notes-on-api-functions-odbc-driver-for-oracle"></a>Thread Safety note sulle funzioni API (Driver ODBC per Oracle)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. In alternativa, utilizzare il driver ODBC fornito da Oracle.  
  
 Il Driver ODBC di Microsoft per Oracle è thread-safe. Tuttavia, Oracle non consente più istruzioni simultanee in una singola connessione. Il driver applica questa limitazione. In altre parole, nelle applicazioni multithreading, sebbene qualsiasi thread può effettuare chiamate nel Driver ODBC per Oracle in qualsiasi momento, il driver blocca altri thread dal driver nella stessa connessione finché il thread originale lascia il driver.  
  
 Il driver non si blocca se sono presenti due istruzioni in due diverse connessioni. Tuttavia, se è presente una singola connessione con due istruzioni, è possibili per il blocco.

