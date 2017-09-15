---
title: "Attività driver | Documenti Microsoft"
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 331e3aee3a4a60cbfa1a1308b71da80bf9772f23
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="driver-tasks"></a>Attività di driver
Attività specifiche eseguite da tutti i driver includono:  
  
-   Alla connessione e disconnessione dall'origine dati.  
  
-   Il controllo degli errori di funzione non controllati da Gestione Driver.  
  
-   Avvio di transazioni. Questo è trasparente all'applicazione.  
  
-   Invio di istruzioni SQL per l'origine dati per l'esecuzione. Il driver è necessario modificare SQL ODBC per SQL specifici del DBMS. Questo è spesso limitato alla sostituzione di clausole di escape definite da ODBC con SQL DBMS specifici.  
  
-   L'invio dei dati e il recupero dei dati dall'origine dati, tra cui la conversione di tipi di dati come specificato dall'applicazione.  
  
-   Errori specifici del DBMS di mapping di SQLSTATE ODBC.
