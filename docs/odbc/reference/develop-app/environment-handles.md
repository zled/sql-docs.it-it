---
title: Handle di ambiente | Documenti Microsoft
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
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ffbc2ed4c1c496833237c3bda6d6e2c306a50cac
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="environment-handles"></a>Handle di ambiente
Un *ambiente* è un contesto in cui si desidera accedere ai dati globale, associata a un ambiente è qualsiasi informazione che è globale in natura, ad esempio:  
  
-   Stato dell'ambiente  
  
-   La diagnostica a livello di ambiente corrente  
  
-   Gli handle di connessioni attualmente allocate sull'ambiente  
  
-   Le impostazioni correnti di ogni attributo di ambiente  
  
 All'interno di un frammento di codice che implementa ODBC (Driver Manager o un driver), un handle di ambiente identifica una struttura per contenere queste informazioni.  
  
 Handle di ambiente non vengono spesso utilizzati nelle applicazioni ODBC. Vengono sempre utilizzati nelle chiamate a **SQLDataSources** e **SQLDrivers** e a volte usato in chiamate a **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**, e **SQLGetDiagRec**.  
  
 Ogni frammento di codice che implementa ODBC (Driver Manager o un driver) contiene uno o più handle di ambiente. Ad esempio, il gestore di Driver gestisce un handle di ambiente separato per ogni applicazione che è connesso. Handle di ambiente vengono allocati con **SQLAllocHandle** e liberata con **SQLFreeHandle**.
