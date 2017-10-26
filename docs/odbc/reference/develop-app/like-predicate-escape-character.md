---
title: COME carattere di Escape predicato | Documenti Microsoft
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
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 132359972cebd3dded36fb911a2ee8e561e5ca64
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="like-predicate-escape-character"></a>COME carattere di Escape predicato
In un **come** predicato, il segno di percentuale (%) corrispondenze zero o più di qualsiasi carattere e il carattere di sottolineatura (_) consente di ricercare qualsiasi carattere. In base a un segno di percentuale effettivo o un carattere di sottolineatura un **come** predicato, un carattere di escape deve precedere il segno di percentuale o un carattere di sottolineatura. La sequenza di escape che definisce il **come** carattere di escape del predicato è:  
  
 **{escape '** *carattere di escape* **'}**  
  
 dove *carattere di escape* è qualsiasi carattere supportato dall'origine dati.  
  
 Per altre informazioni simili sequenza di escape, vedere [come sequenza di Escape](../../../odbc/reference/appendixes/like-escape-sequence.md) nella grammatica SQL di appendice c:.  
  
 Le istruzioni SQL seguenti, ad esempio, creano lo stesso set di risultati di cliente nomi che iniziano con i caratteri "% AAA". La prima istruzione utilizza la sintassi della sequenza di escape. La seconda istruzione utilizza la sintassi nativa per Microsoft® Access e non è interoperativa. Si noti che la percentuale del secondo carattere in ogni **come** predicato è composto da un carattere jolly che corrisponde a zero o più di qualsiasi carattere.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Per determinare se il **come** carattere di escape del predicato è supportata da un'origine dati, un'applicazione chiama **SQLGetInfo** con l'opzione SQL_LIKE_ESCAPE_CLAUSE.

