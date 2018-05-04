---
title: COME sequenza di Escape | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a9ae849aa255b5427d1efca50d6e429ee6a2afb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="like-escape-sequence"></a>COME sequenza di Escape
ODBC utilizza le sequenze di escape per la clausola LIKE. La sintassi di questa sequenza di escape è come segue:  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Osservazioni  
 Nella notazione BNF, la sintassi è:  
  
 *ODBC-like-escape* :: =  
  
 *ODBC-esc-iniziatore* escape '*carattere di escape*' *ODBC-esc-carattere di terminazione*  
  
 *carattere di escape* :: = *carattere*  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *ODBC-esc-carattere di terminazione* :: =}  
  
 Per determinare se il driver supporta il carattere di escape LIKE sequenza, un'applicazione può chiamare **SQLGetInfo** con il tipo di informazioni SQL_LIKE_ESCAPE_CLAUSE.
