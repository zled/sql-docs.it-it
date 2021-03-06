---
title: Handle di ambiente | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a73ec4a842e220a16189f1390df167fe12bbab8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692259"
---
# <a name="environment-handles"></a>Handle di ambiente
Un' *ambiente* è un contesto globale in cui si desidera accedere ai dati; associato a un ambiente è qualsiasi informazione che è globale in natura, ad esempio:  
  
-   Stato dell'ambiente  
  
-   La diagnostica a livello di ambiente corrente  
  
-   Gli handle di connessioni attualmente allocate nell'ambiente  
  
-   Le impostazioni correnti di ogni attributo di ambiente  
  
 All'interno di un frammento di codice che implementa ODBC (gestione Driver o un driver), un handle di ambiente identifica una struttura per contenere tali informazioni.  
  
 Handle di ambiente non vengono spesso usati nelle applicazioni ODBC. Vengono sempre usati nelle chiamate a **SQLDataSources** e **SQLDrivers** e a volte usati nelle chiamate a **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**, e **SQLGetDiagRec**.  
  
 Ogni frammento di codice che implementa ODBC (gestione Driver o un driver) contiene uno o più handle di ambiente. Ad esempio, gestione Driver mantiene un handle di ambiente separati per ogni applicazione che vi è connesso. Handle di ambiente vengono allocati con **SQLAllocHandle** e liberati con **SQLFreeHandle**.
