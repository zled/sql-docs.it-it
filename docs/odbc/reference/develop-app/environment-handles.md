---
title: Handle di ambiente | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a84e7d5939eb4d4c57b7f59db6d719627cf4be3b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
