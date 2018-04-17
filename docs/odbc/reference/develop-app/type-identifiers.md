---
title: Gli identificatori dei tipi | Documenti Microsoft
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
- data types [ODBC], identifiers
- type identifiers [ODBC]
- identifiers [ODBC], type
- type identifiers [ODBC], about type identifiers
ms.assetid: 1d9fdfa2-e378-44fe-ac66-9743d9bbdd5a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a3de97dbf1ce632f1204a2218ead0c7ddd8cdf2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="type-identifiers"></a>Identificatori di tipo
Per descrivere i tipi di dati SQL e C, ODBC definisce due insiemi di *gli identificatori dei tipi*. Un identificatore di tipo descrive il tipo di una colonna SQL o di un buffer di C. Si tratta di un **#define** valore e viene in genere passato come argomento di funzione o restituito nei metadati.  
  
 Ad esempio, la seguente chiamata al **SQLBindParameter** associa una variabile di tipo valore SQL_DATE_STRUCT a un parametro di data in un'istruzione SQL. L'identificatore di tipo C SQL_C_TYPE_DATE specifica il tipo di *data* variabile e l'identificatore del tipo SQL_TYPE_DATE SQL specifica il tipo del parametro dinamico.  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER  DateInd = 0;  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_TYPE_DATE, SQL_TYPE_DATE, 0, 0,  
                  &Date, 0, &DateInd);  
```
