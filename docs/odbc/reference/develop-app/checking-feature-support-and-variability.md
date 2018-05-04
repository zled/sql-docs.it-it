---
title: Verifica il supporto di funzionalità e la variabilità | Documenti Microsoft
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
- interoperability [ODBC], feature support and variability
- interoperability [ODBC], writing interoperable applications
- feature support in interoperable applications [ODBC]
- feature variability in interoperable applications [ODBC]
ms.assetid: ff45f220-9b8b-4c44-82f8-a8e9913fffea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 82b8a0c2c50e557e055ef14a4ac34a486611304d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="checking-feature-support-and-variability"></a>Verifica il supporto di funzionalità e la variabilità
Per verificare il supporto di funzionalità e la variabilità, chiamano in genere applicazioni **SQLGetInfo**, **SQLGetFunctions**, e **SQLGetTypeInfo**. Un buon punto di partenza è SQL e API grammatica livelli di conformità del driver. In cui sono descritti ampi livelli di supporto della funzionalità. L'applicazione può quindi chiamare **SQLGetInfo** con altre opzioni per determinare il supporto tecnico o variabilità delle funzionalità necessarie, **SQLGetFunctions** per determinare se le funzioni è necessario oltre restituito livello di conformità sono supportati, e **SQLGetTypeInfo** per determinare quali tipi di dati SQL sono supportati.  
  
 Un'applicazione può determinare se un attributo di istruzione o connessione è supportato tramite la chiamata **SQLSetStmtAttr** o **SQLSetConnectAttr** con tale attributo. Se la funzione restituisce SQL_SUCCESS o SQL_SUCCESS_WITH_INFO, l'attributo è supportato; Se viene restituito SQL_ERROR e SQLSTATE HYC00 (funzionalità facoltativa non implementata), l'attributo non è supportato.  
  
 Le applicazioni possono inoltre determinare una quantità limitata di informazioni prima della connessione al driver chiamando **SQLDrivers**.
