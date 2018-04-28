---
title: Metodo getSQLStateType (SQLServerDatabaseMetaData) | Documenti Microsoft
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
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9090d0632c82a811d0c03fdc98dae44c0a732db
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>Metodo getSQLStateType (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se il valore SQLSTATE restituito dal metodo SQLException.getSQLState è X/Open (ora noto come Open Group), SQL CLI, SQL99 (JDBC 3.0) o SQL:2003 (JDBC 4.0).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il tipo di SQLSTATE, che può essere uno dei valori seguenti:  
  
-   Per Java Runtime Environment versione 5.0: se il **xopenStates** connessione è impostata su **true**, questo metodo restituisce DatabaseMetaData.sqlStateXOpen. In caso contrario, DatabaseMetaData.sqlStateSQL99.  
  
-   Per Java Runtime Environment versione 6.0: se il **xopenStates** connessione è impostata su **true**, questo metodo restituisce DatabaseMetaData.sqlStateXOpen. In caso contrario, DatabaseMetaData.sqlStateSQL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getSQLStateType viene specificato dal metodo getSQLStateType nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
