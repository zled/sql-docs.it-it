---
title: Metodo getNString (int) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2048bb9f-7d9b-4aaa-b135-c716910cc800
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d79069f86158b6ec70557780c7c936b4d6f686d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getnstring-method-int"></a>Metodo getNString (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del tipo designato **NCHAR**, **NVARCHAR**, o **LONGNVARCHAR** parametro sotto forma di stringa nel linguaggio linguaggio di programmazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final java.lang.String getNString(int parameterIndex)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterIndex*  
  
 Un **int** che indica l'indice del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 AStringobject.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getNString viene specificato dal metodo getNString nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getNString &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
