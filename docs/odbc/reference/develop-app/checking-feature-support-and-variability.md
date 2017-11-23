---
title: "Verifica il supporto di funzionalità e la variabilità | Documenti Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31b297b5d1932c6e3a9c8b7e128973d36fbd93cd
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="checking-feature-support-and-variability"></a>Verifica il supporto di funzionalità e la variabilità
Per verificare il supporto di funzionalità e la variabilità, chiamano in genere applicazioni **SQLGetInfo**, **SQLGetFunctions**, e **SQLGetTypeInfo**. Un buon punto di partenza è SQL e API grammatica livelli di conformità del driver. In cui sono descritti ampi livelli di supporto della funzionalità. L'applicazione può quindi chiamare **SQLGetInfo** con altre opzioni per determinare il supporto tecnico o variabilità delle funzionalità necessarie, **SQLGetFunctions** per determinare se le funzioni è necessario oltre restituito livello di conformità sono supportati, e **SQLGetTypeInfo** per determinare quali tipi di dati SQL sono supportati.  
  
 Un'applicazione può determinare se un attributo di istruzione o connessione è supportato tramite la chiamata **SQLSetStmtAttr** o **SQLSetConnectAttr** con tale attributo. Se la funzione restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, l'attributo è supportato; Se viene restituito SQL_ERROR e SQLSTATE HYC00 (funzionalità facoltativa non implementata), l'attributo non è supportato.  
  
 Le applicazioni possono inoltre determinare una quantità limitata di informazioni prima della connessione al driver chiamando **SQLDrivers**.
