---
title: Esempio di diagnostica di Gestione driver | Documenti Microsoft
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
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b5abbaad714c483a67bd4e3de547449ef358e68
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="driver-manager-diagnostic-example"></a>Esempio di diagnostica di Gestione driver
Gestione Driver è anche possibile generare messaggi di diagnostica. Ad esempio, se un'applicazione passata un'opzione di direzione non valida per **SQLDataSources**, gestione Driver potrebbe formattare e restituire i valori seguenti dal **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Si è verificato l'errore in Gestione Driver, aggiungere prefissi per il messaggio di diagnostica per il fornitore ([Microsoft]) e il relativo identificatore ([gestione Driver ODBC]).
