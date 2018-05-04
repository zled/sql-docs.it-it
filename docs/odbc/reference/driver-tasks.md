---
title: Attività driver | Documenti Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c7e351a84272e8ab9bd558e93e0d12bdc8275884
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="driver-tasks"></a>Attività di driver
Attività specifiche eseguite da tutti i driver includono:  
  
-   Alla connessione e disconnessione dall'origine dati.  
  
-   Il controllo degli errori di funzione non controllati da Gestione Driver.  
  
-   Avvio di transazioni. Questo è trasparente all'applicazione.  
  
-   Invio di istruzioni SQL per l'origine dati per l'esecuzione. Il driver è necessario modificare SQL ODBC per SQL specifici del DBMS. Questo è spesso limitato alla sostituzione di clausole di escape definite da ODBC con SQL DBMS specifici.  
  
-   L'invio dei dati e il recupero dei dati dall'origine dati, tra cui la conversione di tipi di dati come specificato dall'applicazione.  
  
-   Errori specifici del DBMS di mapping di SQLSTATE ODBC.
