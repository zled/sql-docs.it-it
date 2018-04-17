---
title: Restituendo SQL_NO_DATA | Documenti Microsoft
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
- SQL_NO_DATA [ODBC]
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0163c8e9d8c207d2ce8a7ae80c4ec03d9b7c64e2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="returning-sqlnodata"></a>Restituendo SQL_NO_DATA
Quando un'applicazione ODBC 2. *x* applicazione con un'applicazione ODBC 3*x* driver chiama **SQLExecDirect**, **SQLExecute**, o **SQLParamData**, e un aggiornamento con ricerca o l'istruzione delete è stato eseguito ma non ha influito sulle righe nell'origine dei dati ODBC 3*x* driver restituisce SQL_SUCCESS. Quando un'applicazione ODBC 3*x* applicazione che utilizza un'applicazione ODBC 3*x* driver chiama **SQLExecDirect**, **SQLExecute**, o  **SQLParamData** con lo stesso risultato, ODBC 3*x* driver restituisce SQL_NO_DATA.  
  
 Se una ricerca istruzioni update o delete in un batch di istruzioni non influiscono su tutte le righe nell'origine dati, **SQLMoreResults** restituisce SQL_SUCCESS. Non può restituire SQL_NO_DATA, perché il che significa che non sono presenti altri risultati, non che vi è un risultato da un update/delete con ricerca che non le righe interessate.
