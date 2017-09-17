---
title: SQLSetStmtOption (driver di Database Desktop) | Documenti Microsoft
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
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8d1f51805413056a06c6cee769920e1ad878abe5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption (driver di Database Desktop)
|*fOption*|Commenti|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|Non è supportata l'elaborazione asincrona. Il parametro fOption SQL_ASYNC_ENABLE restituiranno SQLSTATE S1C00 (Driver non valido).|  
|SQL_KEYSET_SIZE|La dimensione del keyset solo valido è 0, poiché misto e i cursori dinamici non sono supportati. Se questo valore è impostato su qualsiasi altro numero, verrà modificata su 0 e la chiamata restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE 01S02 (valore di opzione modificato).|  
|SQL_MAX_ROWS|Le dimensioni del set di righe solo valido sono 0, poiché i driver di Database Desktop non supportano limitando il numero di righe restituite. Se questo valore è impostato su qualsiasi altro numero, verrà modificata su 0 e la chiamata restituisce SQL_SUCCESS_WITH_INFO e SQLSTATE 01S02 (valore di opzione modificato).|  
|SQL_QUERY_TIMEOUT|Non supportato.|  
|SQL_ROW_NUMBER|Non supportato.|  
|SQL_SIMULATE_CURSOR|Non supportato.|
