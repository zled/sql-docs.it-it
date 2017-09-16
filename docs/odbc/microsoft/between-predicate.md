---
title: TRA predicato | Documenti Microsoft
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
- BETWEEN predicate [ODBC]
- SQL grammar [ODBC], between predicate
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8daaa0e1c26f00acbff2e6f7788eab8ee5ac8ce
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="between-predicate"></a>TRA predicato
La sintassi seguente:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Restituisce true solo se *expression1* è maggiore o uguale a *expression2* e *expression1* è minore o uguale a *expression3*.  
  
 La semantica di questa sintassi è diversa per i driver di Database Desktop e gestione di Microsoft Jet. In SQL di Microsoft Jet, *expression2* può essere maggiore di *expression3* in modo che l'istruzione restituirà TRUE solo se *expression1* è maggiore o uguale a *expression3*, e *expression1* è minore o uguale a *expression2*.
