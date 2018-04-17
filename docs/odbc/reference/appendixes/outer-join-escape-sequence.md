---
title: Sequenza di Escape di outer Join | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 71205972831d4a0370a0905aeaa8f94d9639894e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="outer-join-escape-sequence"></a>Sequenza di Escape di outer Join
ODBC utilizza le sequenze di escape per gli outer join. La sintassi di questa sequenza di escape è come segue:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Osservazioni  
 Nella notazione BNF, la sintassi è:  
  
 *ODBC-outer-join-escape* :: =  
  
 *ODBC-esc-iniziatore* GU *outer join ODBC esc-carattere di terminazione*  
  
 *outer join* :: = *-nome della tabella* [*nome di correlazione*] {sinistra &#124; a destra &#124; completo}  
  
 OUTER JOIN {*-nome della tabella* [*nome di correlazione*] &#124; *outer join*} ON  
  
 *ricerca-*  
  
 *Condizione*  
  
 *nome di correlazione* :: = *nome definito dall'utente*  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *ODBC-esc-carattere di terminazione* :: =}  
  
 Per determinare quali parti di questa istruzione sono supportate, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_OJ_CAPABILITIES. Per gli outer join, *condizione di ricerca* deve contenere solo la condizione di join tra l'oggetto specificato *i nomi di tabella*.
