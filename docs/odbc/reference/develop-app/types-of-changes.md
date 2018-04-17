---
title: Tipi di modifiche | Documenti Microsoft
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
- compatibility [ODBC], types of changes
- backward compatibility [ODBC], types of changes
ms.assetid: 6a7db81a-20aa-4915-aed8-429711a36f49
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f3db03bfda3e464ebc422cbbc009c586e83863b6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="types-of-changes"></a>Tipi di modifiche
Tre tipi di modifiche vengono apportati in ODBC 3. *x* (e qualsiasi versione di ODBC). Ognuna di queste influisce sulla compatibilità con le versioni precedenti in modo diverso e viene gestita in modo diverso. Tali modifiche sono descritte nella tabella seguente.  
  
|Tipo di modifica|Description|  
|--------------------|-----------------|  
|Nuove funzionalità|Si tratta di funzioni che hanno familiarità con ODBC 3. *x*, ad esempio descrittori o associazione out-of-line. Sono implementati solo quando l'applicazione e driver, nonché gestione Driver versione 3*x*, pertanto non c'è alcun tentativo di rendere questi compatibile con le versioni precedenti.|  
|Funzionalità di duplicati|Si tratta di funzionalità che esistono in ODBC 2*x* mentre ODBC 3. *x* ma vengono implementati in modi diversi in ogni. Le funzioni **SQLAllocHandle** e **SQLAllocStmt** sono un esempio. Problemi di compatibilità con le versioni precedenti per queste e altre funzionalità duplicati vengono principalmente gestiti dal mapping in Gestione Driver.|  
|Modifiche del comportamento|Si tratta di funzionalità che sono gestite diversamente in ODBC 2*x* mentre ODBC 3. *x*. Un valore datetime **#define** è riportato un esempio. Queste funzionalità vengono gestite da ODBC 3. *x* driver in base a un'impostazione dell'attributo di ambiente. (Vedere [modifiche del comportamento](../../../odbc/reference/develop-app/behavioral-changes.md) per ulteriori informazioni.)|
