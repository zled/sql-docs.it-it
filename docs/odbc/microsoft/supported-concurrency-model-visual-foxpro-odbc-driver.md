---
title: "È supportato il modello di concorrenza, Driver ODBC di Visual FoxPro | Documenti Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 769c6efaf95b1642209fa46b292822914261b826
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>Modello di concorrenza supportate (Visual FoxPro ODBC Driver)
Il Driver ODBC di Visual FoxPro supporta *concorrenza di sola lettura*. L'applicazione può chiamare [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) con un'opzione SQL_CONCURRENCY di SQL_CONCUR_READ_ONLY.  
  
 Per ulteriori informazioni, vedere il [riferimento per programmatori ODBC](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>concorrenza di sola lettura  
 Impossibile aggiornare il cursore.  
  
## <a name="row-versioning"></a>controllo delle versioni delle righe  
 Essenzialmente timestamp supporto, nella quale riga versioni vengono confrontate in fase di aggiornamento.
