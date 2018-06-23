---
title: SQLCancel | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6aff7aea0040e2fd7f86a3ad668b4e4438148497
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168997"
---
# <a name="sqlcancel"></a>SQLCancel
  Il [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516) argomento indica che in ODBC 2.x, se un'applicazione chiama `SQLCancel` quando non viene fatta alcuna elaborazione nell'istruzione `SQLCancel` ha lo stesso effetto `SQLFreeStmt` con il `SQL_CLOSE` opzione; in questo comportamento viene definito solo per motivi di completezza e le applicazioni devono chiamare `SQLFreeStmt` o `SQLCloseCursor` per chiudere i cursori. Tuttavia, anche se l'applicazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client consente di impostare la versione dell'API ODBC 3.5.x o successiva, nella funzione `SQLCancel` verrà utilizzato il comportamento ODBC 2.x.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLCancel](http://go.microsoft.com/fwlink/?LinkId=203516)   
 [Dettagli di implementazione dell'API ODBC](odbc-api-implementation-details.md)  
  
  