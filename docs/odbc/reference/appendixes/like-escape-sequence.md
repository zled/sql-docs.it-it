---
title: COME sequenza di Escape | Documenti Microsoft
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
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37733aadb069cd161427fc8f186647cfba030b6d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32906506"
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
