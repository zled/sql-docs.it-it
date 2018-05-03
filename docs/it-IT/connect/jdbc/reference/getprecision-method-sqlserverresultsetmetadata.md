---
title: Metodo getPrecision (SQLServerResultSetMetaData) | Documenti Microsoft
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
- SQLServerResultSetMetaData.getPrecision
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de46c96e-6ad6-4946-883e-807123658500
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c75e0a2f1c9350497e0e27ded2b9242f174f6db
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getprecision-method-sqlserverresultsetmetadata"></a>Metodo getPrecision (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ottiene il numero di cifre decimali della colonna designata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getPrecision(int column)  
```  
  
#### <a name="parameters"></a>Parametri  
 *column*  
  
 Un **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica la precisione della colonna.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getPrecision viene specificato dal metodo getPrecision nell'interfaccia Java.SQL. ResultSetMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membri di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Classe SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
