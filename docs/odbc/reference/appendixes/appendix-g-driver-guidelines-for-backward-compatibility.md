---
title: 'Appendice g: Driver le linee guida per la compatibilità con le versioni precedenti | Documenti Microsoft'
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
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e84628c88937674ae5b2c1c992a40a8d3396cc2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Appendice g: Driver le linee guida per la compatibilità con le versioni precedenti
Questa appendice vengono fornite informazioni per gli sviluppatori di driver lavorando ODBC 3. *x* driver che necessitano di supporto ODBC 2. *x* applicazioni. Per ulteriori informazioni sulla compatibilità, vedere [compatibilità e conformità agli standard](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Cursori a blocchi, i cursori scorrevoli e la compatibilità con le versioni precedenti per driver ODBC 3.x](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) : nuove funzionalità sono le funzionalità disponibili in ODBC 3. *x* e non in ODBC 2. *x*. ODBC 3. *x* driver in genere non è necessario preoccuparsi di garantire la compatibilità con le nuove funzionalità in quanto l'API ODBC 2. *x* mai utilizzano applicazioni. Le eccezioni a questa unica sono le funzionalità correlate a **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, e **SQLExtendedFetch**; per ulteriori informazioni informazioni, vedere più avanti in questa appendice.  
  
-   [Mapping di funzioni deprecate](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) : funzionalità duplicato sono implementati in modo diverso in ODBC 3. *x* e ODBC 2. *x*. ODBC 3. *x* driver non è necessario preoccuparsi di garantire la compatibilità con le funzionalità di duplicati perché è sempre mappata gestione Driver ODBC 2. *x* funzionalità ODBC 3. *x* funzionalità quando si chiama un'applicazione ODBC 3. *x* driver. Di conseguenza, un database ODBC 3. *x* driver vede solo ODBC 3. *x* funzionalità. Per ulteriori informazioni su tali mapping, vedere, più avanti in questa appendice.  
  
-   [Modifiche del comportamento e i driver ODBC 3.x](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) : le modifiche del comportamento sono funzionalità che vengono gestite in modo diverso in ODBC 3. *x* e ODBC 2. *x*. ODBC 3. *x* driver sono necessario preoccuparsi delle modifiche di comportamento e agire in risposta all'attributo SQL_ATTR_ODBC_VERSION ambiente impostata dall'applicazione.
