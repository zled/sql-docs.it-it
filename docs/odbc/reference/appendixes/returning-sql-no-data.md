---
title: Restituendo SQL_NO_DATA | Documenti Microsoft
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
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
ms.assetid: deed0163-9d1a-4e9b-9342-3f82e64477d2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5539f9d2951913163ac6011695709e3664d8acb1
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="returning-sqlnodata"></a>Restituendo SQL_NO_DATA
Quando un'applicazione ODBC 2. *x* applicazione con un'applicazione ODBC 3*x* driver chiama **SQLExecDirect**, **SQLExecute**, o **SQLParamData**, e un aggiornamento con ricerca o l'istruzione delete è stato eseguito ma non ha influito sulle righe nell'origine dei dati ODBC 3*x* driver restituisce SQL_SUCCESS. Quando un'applicazione ODBC 3*x* applicazione che utilizza un'applicazione ODBC 3*x* driver chiama **SQLExecDirect**, **SQLExecute**, o ** SQLParamData** con lo stesso risultato, ODBC 3*x* driver restituisce SQL_NO_DATA.  
  
 Se una ricerca istruzioni update o delete in un batch di istruzioni non influiscono su tutte le righe nell'origine dati, **SQLMoreResults** restituisce SQL_SUCCESS. Non può restituire SQL_NO_DATA, perché il che significa che non sono presenti altri risultati, non che vi è un risultato da un update/delete con ricerca che non le righe interessate.

