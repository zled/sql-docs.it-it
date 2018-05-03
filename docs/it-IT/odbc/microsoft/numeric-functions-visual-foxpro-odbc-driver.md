---
title: Funzioni numeriche, Driver ODBC di Visual FoxPro | Documenti Microsoft
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
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42d494823cf1792bbec78ff3de1d70d4f8f75046
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>Funzioni numeriche, Driver ODBC di Visual FoxPro,
La tabella seguente descrive le funzioni ODBC numeriche supportate dal Driver ODBC di Visual FoxPro; Quando la grammatica di Visual FoxPro per la stessa funzione differisce dalla sintassi ODBC, viene elencata l'equivalente di Visual FoxPro.  
  
|Grammatica ODBC|Grammatica di Visual FoxPro|  
|------------------|---------------------------|  
|ABS *(numeric_exp)*||  
|ACOS *(float_exp)*||  
|ASIN *(float_exp)*||  
|ATAN *(float_exp)*||  
|Atan2 *(float_exp1, float_exp2)*|ATN2 (*float_exp1, float_exp2*)|  
|CEILING *(numeric_exp)*||  
|COS *(float_exp)*||  
|COT *(float_exp)*||  
|GRADI *(numeric_exp)*|RTOD *(numeric_exp)*|  
|EXP *(float_exp)*||  
|FLOOR *(numeric_exp)*||  
|LOG *(float_exp)*||  
|LOG10 *(float_exp)*||  
|MOD *(integer_exp1, integer_exp2)*||  
|PI *)*||  
|RADIANTI *(numeric_exp)*|DTOR *(numeric_exp)*|  
|RAND *([integer_exp])*||  
|ARROTONDAMENTO *(numeric_exp, integer_exp)*||  
|SIGN *(numeric_exp)*||  
|SIN *(float_exp)*||  
|SQRT *(float_exp)*||  
|TAN *(float_exp)*||  
  
 Le funzioni numeriche seguenti non sono supportate:  
  
 POWER *(numeric_exp, integer_exp)*  
  
 TRONCARE *(numeric_exp, integer_exp)*
