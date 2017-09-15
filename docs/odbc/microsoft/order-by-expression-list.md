---
title: ORDERBY-elenco di espressioni | Documenti Microsoft
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
- ORDER BY clause [ODBC]
- SQL grammar [ODBC], order by clause
ms.assetid: 5ef88186-a99f-4e2c-a3f3-98a42d4f03a5
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b64ad53abb02d04077548a1b4483d89307b0a5a0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="order-by-expression-list"></a>ORDERBY-elenco di espressioni
Le espressioni possono essere utilizzate nella clausola ORDER BY. Ad esempio, nelle clausole seguenti nella tabella viene ordinata in base tre espressioni chiave: + b, c + d ed e.  
  
```  
SELECT * FROM emp  
ORDER BY a+b,c+d,e  
```  
  
 Nessun ordinamento è consentito nel set di funzioni o un'espressione che contiene una funzione set.
