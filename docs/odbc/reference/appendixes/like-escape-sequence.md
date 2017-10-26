---
title: COME sequenza di Escape | Documenti Microsoft
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
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 678f2f8f720823ef5658ba7ee1e1391bbebc1c50
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="like-escape-sequence"></a>COME sequenza di Escape
ODBC utilizza le sequenze di escape per la clausola LIKE. La sintassi di questa sequenza di escape è come segue:  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Osservazioni  
 Nella notazione BNF, la sintassi è:  
  
 *Caratteri di tipo ODBC escape* :: =  
  
 *ODBC-esc-iniziatore* escape '*carattere di escape*' *ODBC-esc-carattere di terminazione*  
  
 *carattere di escape* :: = *carattere*  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *Terminatore di esc ODBC* :: =}  
  
 Per determinare se il driver supporta il carattere di escape LIKE sequenza, un'applicazione può chiamare **SQLGetInfo** con il tipo di informazioni SQL_LIKE_ESCAPE_CLAUSE.

