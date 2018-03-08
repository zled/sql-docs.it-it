---
title: Funzioni numeriche | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions [ODBC], numeric functions
- numeric functions [ODBC]
ms.assetid: 4fa548dc-e8b0-4179-92ff-81d6a79d10c3
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8a4b3c0cca843e576fd200b6803db8f1bac5adcb
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="numeric-functions"></a>Funzioni numeriche
La tabella seguente descrive le funzioni numeriche inclusi nel set di funzioni scalari ODBC. Chiamando **SQLGetInfo** con un *tipo di informazioni* di SQL_NUMERIC_FUNCTIONS, un'applicazione può determinare quali funzioni numeriche sono supportate da un driver.  
  
 Tutte le funzioni numeriche restituiscono i valori del tipo di dati SQL_FLOAT ABS, ad eccezione di arrotondamento, TRUNCATE, SIGN, FLOOR e CEILING, che restituiscono i valori degli stessi dati di tipo come parametri di input.  
  
 Gli argomenti indicati come *numeric_exp* può essere il nome di una colonna, il risultato di un'altra funzione scalare, o un *numerico litera*l, dove il tipo di dati sottostante potrebbe essere rappresentato come SQL_NUMERIC, SQL _ DECIMALE, SQL_TINYINT, SQL_SMALLINT, SQL_INTEGER, SQL_BIGINT, SQL_FLOAT, SQL_REAL o SQL_DOUBLE.  
  
 Gli argomenti indicati come *float_exp* può essere il nome di una colonna, il risultato di un'altra funzione scalare, o un *valore letterale numerico*, in cui il tipo di dati sottostante può essere rappresentato come SQL_FLOAT.  
  
 Gli argomenti indicati come *integer_exp* può essere il nome di una colonna, il risultato di un'altra funzione scalare, o un *valore letterale numerico*, in cui il tipo di dati sottostante può essere rappresentato come SQL_TINYINT, SQL _ SMALLINT SQL_INTEGER o SQL_BIGINT.  
  
 Le funzioni scalari CURRENT_DATE CURRENT_TIME e CURRENT_TIMESTAMP sono state aggiunte in ODBC 3.0 per la compatibilità con SQL-92.  
  
|Funzione|Description|  
|--------------|-----------------|  
|**ABS (** *numeric_exp* **)** (ODBC 1.0)|Restituisce il valore assoluto di *numeric_exp*.|  
|**ACOS (** *float_exp* **)** (ODBC 1.0)|Restituisce l'arcocoseno di *float_exp* come un angolo, espresso in radianti.|  
|**ASIN (** *float_exp* **)** (ODBC 1.0)|Restituisce l'arcoseno di *float_exp* come un angolo, espresso in radianti.|  
|**ATAN (** *float_exp* **)** (ODBC 1.0)|Restituisce l'arcotangente di *float_exp* come un angolo, espresso in radianti.|  
|**Atan2 (** *float_exp1*, *float_exp2***)** (ODBC 2.0)|Restituisce l'arcotangente del *x* e *y* coordinate, specificate da *float_exp1* e *float_exp2*, rispettivamente, come un angolo, espresso in radianti.|  
|**CEILING (** *numeric_exp* **)** (ODBC 1.0)|Restituisce l'intero minimo maggiore o uguale a *numeric_exp*. Il valore restituito è dello stesso tipo di dati come parametro di input.|  
|**COS (** *float_exp* **)** (ODBC 1.0)|Restituisce il coseno di *float_exp*, dove *float_exp* è l'angolo, espresso in radianti.|  
|**COT (** *float_exp* **)** (ODBC 1.0)|Restituisce la cotangente *float_exp*, dove *float_exp* è l'angolo, espresso in radianti.|  
|**GRADI (** *numeric_exp* **)** (ODBC 2.0)|Restituisce il numero di gradi convertito da *numeric_exp* radianti.|  
|**EXP (** *float_exp* **)** (ODBC 1.0)|Restituisce il valore esponenziale di *float_exp*.|  
|**FLOOR (** *numeric_exp* **)** (ODBC 1.0)|Restituisce l'intero massimo minore o uguale a *numeric_exp*. Il valore restituito è dello stesso tipo di dati come parametro di input.|  
|**LOG (** *float_exp* **)** (ODBC 1.0)|Restituisce il logaritmo naturale di *float_exp*.|  
|**LOG10 (** *float_exp* **)** (ODBC 2.0)|Logaritmo restituisce la base 10 di *float_exp*.|  
|**MOD (** *integer_exp1*, *integer_exp2***)** (ODBC 1.0)|Restituisce il resto (modulo) di *integer_exp1* diviso *integer_exp2*.|  
|**PI ()** (ODBC 1.0)|Restituisce il valore costante di pi greco sotto forma di un valore a virgola mobile.|  
|**POWER (** *numeric_exp*, *integer_exp***)** (ODBC 2.0)|Restituisce il valore di *numeric_exp* alla potenza di *integer_exp*.|  
|**RADIANTI (** *numeric_exp* **)** (ODBC 2.0)|Restituisce il numero di radianti convertito da *numeric_exp* gradi.|  
|**RAND (**[*integer_exp*]**)** (ODBC 1.0)|Restituisce un valore a virgola mobile casuale usando *integer_exp* come valore di inizializzazione facoltativo.|  
|**ROUND (** *numeric_exp*, *integer_exp***)** (ODBC 2.0)|Restituisce *numeric_exp* arrotondato *integer_exp* posizionato a destra del separatore decimale. Se *integer_exp* è negativo, *numeric_exp* viene arrotondato a &#124; *integer_exp*&#124; posizioni a sinistra del separatore decimale.|  
|**SIGN (** *numeric_exp* **)** (ODBC 1.0)|Restituisce un indicatore del segno di *numeric_exp*. Se *numeric_exp* è minore di zero, -1 viene restituito. Se *numeric_exp* è uguale a zero, viene restituito 0. Se *numeric_exp* è maggiore di zero, viene restituito 1.|  
|**SIN (** *float_exp* **)** (ODBC 1.0)|Restituisce il seno di *float_exp*, dove *float_exp* è l'angolo, espresso in radianti.|  
|**SQRT (** *float_exp* **)** (ODBC 1.0)|Restituisce la radice quadrata di *float_exp*.|  
|**TAN (** *float_exp* **)** (ODBC 1.0)|Restituisce la tangente di *float_exp*, dove *float_exp* è l'angolo, espresso in radianti.|  
|**TRUNCATE (** *numeric_exp*, *integer_exp***)** (ODBC 2.0)|Restituisce *numeric_exp* troncato a *integer_exp* posizionato a destra del separatore decimale. Se *integer_exp* è negativo, *numeric_exp* viene troncato a &#124; *integer_exp*&#124; posizioni a sinistra del separatore decimale.|
