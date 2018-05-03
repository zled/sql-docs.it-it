---
title: Metodo isCaseSensitive (SQLServerResultSetMetaData) | Documenti Microsoft
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
apiname:
- SQLServerResultSetMetaData.isCaseSensitive
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4db67eb7-7ff2-4fb8-8052-39f699de53ff
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d65c511e2cf49718f1e62a8afb0d6d8efc4c1cc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="iscasesensitive-method-sqlserverresultsetmetadata"></a>Metodo isCaseSensitive (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se per una colonna viene fatta distinzione tra maiuscole e minuscole.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isCaseSensitive(int column)  
```  
  
#### <a name="parameters"></a>Parametri  
 *column*  
  
 Un **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la colonna viene fatta distinzione tra maiuscole e minuscole. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo isCaseSensitive viene specificato dal metodo isCaseSensitive nell'interfaccia Java.SQL. ResultSetMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membri di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Classe SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
