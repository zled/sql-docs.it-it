---
title: Interoperabilità di istruzioni SQL | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC]
- interoperability of SQL statements [ODBC], about interoperability
ms.assetid: 3b24c499-829c-4e65-90cf-a3a0f6d0a186
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 205fd667e8891ba0bab0283c1d112af9d608423b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="interoperability-of-sql-statements"></a>Interoperabilità di istruzioni SQL
Ad esempio il resto di un'applicazione, istruzioni SQL possono essere interoperabili o specifici del DBMS. E come gli altri componenti dell'applicazione, deve essere la scelta della modalità interoperativa istruzioni SQL dipende dal tipo di applicazione. Applicazioni personalizzate hanno meno probabile di utilizzare istruzioni SQL interoperative perché sono in genere progettati per sfruttare le funzionalità di uno o due probabilmente DBMS. Applicazioni generiche utilizzano istruzioni SQL interoperative perché progettate per funzionare con un'ampia gamma di DBMS. E applicazioni verticali in genere rientrano in un punto intermedio, richiedono un certo livello di funzionalità ma in caso contrario, utilizzare istruzioni SQL interoperative.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Scelta di una grammatica SQL](../../../odbc/reference/develop-app/choosing-an-sql-grammar.md)  
  
-   [Creazione di istruzioni SQL interoperative](../../../odbc/reference/develop-app/constructing-interoperable-sql-statements.md)
