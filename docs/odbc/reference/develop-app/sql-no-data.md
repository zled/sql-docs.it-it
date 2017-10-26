---
title: SQL_NO_DATA | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4c42213c629c5fa79cd5c6522f4a36f29f36bd8c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlnodata"></a>SQL_NO_DATA
Quando un'applicazione ODBC 3. *x* applicazione chiama **SQLExecDirect**, **SQLExecute**, o **SQLParamData** in un'API ODBC 2.* x* driver per eseguire un aggiornamento con ricerca o eliminare l'istruzione che non influiscono su tutte le righe nell'origine dati, il driver restituisce SQL_SUCCESS, non SQL_NO_DATA. Quando un'applicazione ODBC 2. *x* o ODBC 3.* x* applicazione che utilizza un'applicazione ODBC 3.* x* driver chiama **SQLExecDirect**, **SQLExecute**, o **SQLParamData** con lo stesso risultato, ODBC 3.* x* driver restituisce SQL_NO_DATA.

