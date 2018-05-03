---
title: SQLSetStmtOption (driver di Database Desktop) | Documenti Microsoft
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
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4689c14c5850b99c64379897bebb248f3aea4643
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
