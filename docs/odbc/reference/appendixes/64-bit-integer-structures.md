---
title: Intero a 64 bit strutture | Documenti Microsoft
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
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8760b771b4ef44f2728c0947504c46a3f7d28910
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="64-bit-integer-structures"></a>Strutture di intero a 64 bit
Il tipo C per gli identificatori di tipo dati SQL_C_SBIGINT e SQL_C_UBIGINT sui compilatori Microsoft C è _int64. Quando si utilizza un compilatore diverso da un compilatore di Microsoft® C, il tipo C potrebbe essere diverso. Se il compilatore supporta interi a 64 bit in modo nativo, il driver o l'applicazione deve definire ODBCINT64 per essere di tipo integer a 64 bit nativo. Se il compilatore non supporta valori integer a 64 bit in modo nativo, un'applicazione o il driver è possibile definire le strutture seguenti per verificare che abbia accesso ai dati:  
  
```  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLUINTEGER dwHighWord;  
} SQLUBIGINT  
  
typedef struct{  
SQLUINTEGER dwLowWord;  
SQLINTEGER sdwHighWord;  
} SQLBIGINT  
```  
  
 Queste strutture devono essere allineate a un limite di 8 byte, in quanto un numero intero a 64 bit è allineato al limite di 8 byte.
