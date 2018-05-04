---
title: Tipi di applicazioni | Documenti Microsoft
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
- upgrading applications [ODBC], application types
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application upgrades [ODBC], application types
- application compatibility issues [ODBC]
ms.assetid: d346a64e-a32c-4153-a40f-5b53c2f57ef2
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c2283c81c1ad5389a8662c14ce79942a3cc4b45
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="types-of-applications"></a>Tipi di applicazioni
Le applicazioni ODBC possono essere classificate come segue:  
  
-   **Pure ODBC 2.**  
     ***x* applicazione** applicazione A 32 bit che:  
  
    -   Chiama solo ODBC 2. *x* funzioni (inclusa la funzione ODBC 1.0 **SQLSetParam**). Questi includono 1 ODBC. *x* le applicazioni che sono state trasferite a 32 bit.  
  
    -   È previsto ODBC 2. *x* comportamento per le funzionalità che hanno subito modifiche del comportamento. (Vedere [modifiche del comportamento](../../../odbc/reference/develop-app/behavioral-changes.md) per ulteriori informazioni.)  
  
    -   Non è stato ricompilato con le intestazioni di ODBC 3.5.  
  
-   **Pure ODBC 2.**  
     ***x* applicazione ricompilate** pure ODBC 2. *x* applicazione che è stato ricompilato utilizzando i file di intestazione ODBC 3.5, impostando ODBCVER = 0x0250.  
  
-   **Pure ODBC 2.**  
     ***x* applicazione Unicode** pure ODBC 2. *x* ricompilate applicazione conforme a Unicode e che utilizza il tipo di dati SQL_WCHAR.  
  
-   **Pure Open Group e ISO**–**applicazione ODBC compatibile** applicazione A 32 bit che:  
  
    -   Chiama funzioni definite negli standard Open Group o ISO CLI. (Queste funzioni possono includere 3.0 funzioni deprecate).  
  
    -   Non utilizzare i tipi di dati Unicode.  
  
    -   Comportamento di ODBC 3.0 per le funzionalità che hanno subito modifiche del comportamento è previsto.  
  
-   **Applicazione ODBC 3.0** applicazione A 32 bit che:  
  
    -   Viene compilato con le 3.0 intestazioni.  
  
    -   Chiama qualsiasi funzione ODBC 3.0, magari con quelli che sono deprecati.  
  
    -   Comportamento di ODBC 3.0 per le funzionalità che hanno subito modifiche del comportamento è previsto.  
  
-   **Applicazione ODBC 3.5** A 32 o 64 bit dell'applicazione che:  
  
    -   Può utilizzare tipi di dati Unicode.  
  
    -   Chiama qualsiasi funzione ODBC 3.5, magari con quelli che sono deprecati.  
  
    -   Comportamento di ODBC 3.5 per le funzionalità che hanno subito modifiche del comportamento è previsto.  
  
-   **ODBC 3.8 (o versioni successive) applicazione** applicazione A 32 bit o 64 bit che:  
  
    -   Può utilizzare tipi di dati Unicode.  
  
    -   Chiama qualsiasi funzione ODBC 3.8, magari con quelli che sono deprecati.  
  
    -   Comportamento di ODBC 3.8 per le funzionalità che hanno subito modifiche del comportamento è previsto.  
  
-   **Sostituito applicazione** A 32 o 64 bit dell'applicazione che:  
  
    -   Implementa nuovo comportamento per funzionalità duplicate.  
  
    -   Utilizza le nuove funzionalità in una versione successiva di ODBC solo all'interno di codice condizionale.  
  
    -   Il codice condizionale per gestire le modifiche del comportamento limitata o è stato registrato da una versione precedente dell'applicazione ODBC.
