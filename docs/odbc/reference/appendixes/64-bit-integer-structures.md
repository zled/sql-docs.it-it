---
title: Intero a 64 bit strutture | Documenti Microsoft
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
- C data types [ODBC], 64-bit integer structures
- data types [ODBC], C data types
- 64-bit integer structures [ODBC]
ms.assetid: ac80c798-d9b2-4430-85ed-bd2461db0ac7
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b267e536535d0df75e1f7c048baa31099c97a704
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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

