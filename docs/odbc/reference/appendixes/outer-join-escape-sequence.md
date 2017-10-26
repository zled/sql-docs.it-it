---
title: Sequenza di Escape di outer Join | Documenti Microsoft
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
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d208b7de815f090e5f61d3d807912c53c4253e31
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="outer-join-escape-sequence"></a>Sequenza di Escape di outer Join
ODBC utilizza le sequenze di escape per gli outer join. La sintassi di questa sequenza di escape è come segue:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Osservazioni  
 Nella notazione BNF, la sintassi è:  
  
 *ODBC outer-join-caratteri di escape* :: =  
  
 *ODBC-esc-iniziatore* GU *outer join ODBC esc-carattere di terminazione*  
  
 *outer join* :: = *-nome della tabella* [*nome di correlazione*] {sinistra &#124; DESTRA &#124; COMPLETA}  
  
 OUTER JOIN {*-nome della tabella* [*nome di correlazione*] &#124; *outer join*} ON  
  
 *ricerca-*  
  
 *condizione*  
  
 *nome di correlazione* :: = *nome definito dall'utente*  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *Terminatore di esc ODBC* :: =}  
  
 Per determinare quali parti di questa istruzione sono supportate, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_OJ_CAPABILITIES. Per gli outer join, *condizione di ricerca* deve contenere solo la condizione di join tra l'oggetto specificato *i nomi di tabella*.

