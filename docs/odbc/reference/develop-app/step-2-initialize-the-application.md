---
title: 'Passaggio 2: Inizializzazione dell''applicazione | Documenti Microsoft'
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
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4b14b5374cedece38295bac840a72acae5895ca8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="step-2-initialize-the-application"></a>Passaggio 2: Inizializzazione dell'applicazione
Il secondo passaggio consiste nella inizializzare l'applicazione, come illustrato nella figura seguente. Esattamente ciò che viene eseguita in questo campo varia con l'applicazione.  
  
 ![Viene illustrata l'inizializzazione di un'applicazione ODBC](../../../odbc/reference/develop-app/media/pr12.gif "pr12")  
  
 A questo punto, è frequente utilizzare **SQLGetInfo** per individuare le funzionalità del driver. Per ulteriori informazioni, vedere [prendere in considerazione le funzionalità di Database da utilizzare](../../../odbc/reference/develop-app/considering-database-features-to-use.md).  
  
 Tutte le applicazioni devono allocare un handle di istruzione con **SQLAllocHandle**, e molte applicazioni di impostavano gli attributi di istruzione, ad esempio il tipo di cursore con **SQLSetStmtAttr**. Per ulteriori informazioni, vedere [allocare un Handle di istruzione](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md) e [gli attributi di istruzione](../../../odbc/reference/develop-app/statement-attributes.md).

