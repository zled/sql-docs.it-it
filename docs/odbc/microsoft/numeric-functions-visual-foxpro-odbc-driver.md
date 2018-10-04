---
title: Funzioni numeriche (Driver ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73379b769da61fe14ba18815446337d0172c2805
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654403"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>Funzioni numeriche (driver ODBC Visual FoxPro)
La tabella seguente descrive le funzioni numeriche ODBC supportate dal Driver ODBC Visual FoxPro; Quando la grammatica di Visual FoxPro per la stessa funzione differisce dalla sintassi ODBC, viene elencato l'equivalente di Visual FoxPro.  
  
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
|La funzione RAND *([integer_exp])*||  
|Funzione ROUND *(numeric_exp, integer_exp)*||  
|SIGN *(numeric_exp)*||  
|SIN *(float_exp)*||  
|SQRT *(float_exp)*||  
|TAN *(float_exp)*||  
  
 Non sono supportate le funzioni numeriche seguenti:  
  
 Risparmio energia *(numeric_exp, integer_exp)*  
  
 TRONCARE *(numeric_exp, integer_exp)*
