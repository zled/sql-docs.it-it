---
title: Sequenza di Escape Outer Join | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ba08d33efca6fa90531f89bd57a307f42f343ebd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47817653"
---
# <a name="outer-join-escape-sequence"></a>Sequenza di escape outer join
ODBC Usa sequenze di escape per gli outer join. La sintassi di questa sequenza di escape è come segue:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Note  
 Nella notazione BNF, la sintassi è come segue:  
  
 *ODBC-outer-join-escape* :: =  
  
 *ODBC-esc-iniziatore* GU *outer join ODBC esc-carattere di terminazione*  
  
 *outer join* :: = *nome tabella* [*correlazione-name*] {sinistra &#124; a destra &#124; completo}  
  
 OUTER JOIN {*-nome della tabella* [*nome di correlazione*] &#124; *outer join*} via  
  
 *ricerca-*  
  
 *Condizione*  
  
 *nome di correlazione* :: = *nome definito dall'utente*  
  
 *ODBC-esc-iniziatore* :: = {  
  
 *ODBC-esc-carattere di terminazione* :: =}  
  
 Per determinare quali parti di questa istruzione sono supportate, un'applicazione chiama **SQLGetInfo** con il tipo di informazioni SQL_OJ_CAPABILITIES. Per gli outer join, *condizione di ricerca* deve contenere solo la condizione di join tra l'oggetto specificato *i nomi di tabella*.
