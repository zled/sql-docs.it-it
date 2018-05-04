---
title: Disconnessione da un tipo di dati origine o il Driver | Documenti Microsoft
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
- disconnecting from driver [ODBC]
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
- connecting to data source [ODBC], disconnecting
- connecting to driver [ODBC], disconnecting
- ODBC drivers [ODBC], disconnecting
ms.assetid: 83dbf0bf-b400-41fb-8537-9b016050dc3c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c99a2fb7c441c6de2a229895a1a68d68e9240c7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="disconnecting-from-a-data-source-or-driver"></a>Disconnessione da un tipo di dati origine o il Driver
Quando un'applicazione ha terminato di utilizzare un'origine dati, chiama **SQLDisconnect**. **SQLDisconnect** libera tutte le istruzioni allocate nella connessione e disconnette il driver dell'origine dati. Restituisce un errore se una transazione è in corso.  
  
 Dopo la disconnessione, l'applicazione può chiamare **SQLFreeHandle** per liberare la connessione. Dopo avere liberato la connessione, è un'applicazione di un errore di programmazione da utilizzare l'handle di connessione in una chiamata a una funzione ODBC; Questa operazione ha conseguenze irreversibili probabilmente ma non definiti. Quando **SQLFreeHandle** viene chiamato, le versioni di driver, la struttura utilizzata per archiviare informazioni di connessione.  
  
 L'applicazione inoltre è possibile riutilizzare la connessione, per connettersi a un'origine dati diversa o riconnettersi alla stessa origine dati. La decisione di rimanere connessi, anziché disconnessione e riconnessione in seguito, è necessario che il writer di applicazione dei costi relativi di ogni opzione. sia la connessione a un'origine dati e rimanere connessi può essere relativamente costosi a seconda del supporto di connessione. Creazione di un compromesso corretto, l'applicazione deve inoltre basarsi su presupposti sulla probabilità e sui tempi di altre operazioni sulla stessa origine dati.
