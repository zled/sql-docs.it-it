---
title: Tipi di driver | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2068bb92d1aaa00debc46277c117d4134091666
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-drivers"></a>Tipi di driver
Driver ODBC possono essere classificati come segue:  
  
-   **32 bit ODBC 2.**  
     ***x* Driver** driver A 32 bit che:  
  
    -   Esporta solo 2 di ODBC*x* funzioni.  
  
    -   Presenta ODBC 2. *x* comportamento per le modifiche di comportamento.  
  
-   **ISO e aprire i Driver compatibili con gruppo** driver A 32 bit che:  
  
    -   Esporta tutte le funzioni che sono documentate nei documenti Open Group o ISO CLI. Questo include alcune delle funzioni che sono deprecate in ODBC.  
  
    -   Comportamento di ODBC 3.0 per modifiche del comportamento.  
  
    -   Non va necessariamente tramite Gestione Driver ODBC 3.0.  
  
-   **Driver ODBC 3.0** driver A 32 bit che:  
  
    -   Esporta le funzioni sole in ODBC 3.0 meno funzioni deprecate.  
  
    -   È in grado di presenta ODBC 2. *x* comportamento o ODBC 3.0 rispetto alle modifiche di comportamento, in base all'attributo di ambiente SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Driver ODBC 3.5 (o versione successiva) ANSI** driver A 32 bit che:  
  
    -   Esporta le funzioni sole in ODBC 3.5 meno funzioni deprecate.  
  
    -   È in grado di presenta ODBC 2. *x* comportamento o comportamento ODBC 3.0 o 3.5 ODBC comportamento rispetto alle modifiche di comportamento, in base all'attributo di ambiente SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Driver ODBC 3.5 (o versione successiva) Unicode** driver A 32 bit che:  
  
    -   Supporta tutte le funzionalità di un driver ODBC 3.5 ANSI.  
  
    -   Esporta le versioni Unicode delle stringa ODBC tutte le API.  
  
    -   Può archiviare ed elaborare i dati Unicode nell'origine dati.  
  
> [!NOTE]  
>  driver ODBC a 16 bit non funzioneranno direttamente con ODBC 3. *x* gestione Driver. Tuttavia, è possibile per i driver a 16 bit a funzionare con il gestore di Driver ODBC 2.0, che successivamente thunk fino a 3. *x* gestione Driver.
