---
title: Mapping SQLBindParam | Documenti Microsoft
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
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 45bd2ccaf64f13e419e7a8da1e772a7d6ad93758
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlbindparam-mapping"></a>Mapping di SQLBindParam
**SQLBindParam** realmente Impossibile chiamare deprecato perché non era presente in ODBC; tuttavia, ancora rappresenta funzionalità duplicate, è necessario esportarlo perché ISO e aprire compatibile con gruppo di applicazioni verranno utilizzato Gestione Driver. Poiché **SQLBindParameter** contiene tutte le funzionalità di **SQLBindParam**, **SQLBindParam** verrà eseguito il mapping in cima **SQLBindParameter** (quando il driver sottostante è un'applicazione ODBC 3*x* driver). Un'applicazione ODBC 3*x* driver non è necessario implementare **SQLBindParam**.  
  
## <a name="remarks"></a>Osservazioni  
 Quando la chiamata seguente a **SQLBindParam** diventa:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 le chiamate di gestione Driver **SQLBindParameter** nel driver come indicato di seguito:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Vedere [informazioni ODBC a 64 Bit](../../../odbc/reference/odbc-64-bit-information.md), se l'applicazione verrà eseguita in un sistema operativo a 64 bit.  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di funzioni deprecate](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
