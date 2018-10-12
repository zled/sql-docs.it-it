---
title: Metodo getSQLStateType (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4a01e2bb8ef76af91c4dede71ae7457351d430b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733199"
---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>Metodo getSQLStateType (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se il valore SQLSTATE restituito dal metodo SQLException.getSQLState è X/Open (ora noto come Open Group), SQL CLI, SQL99 (JDBC 3.0) o SQL:2003 (JDBC 4.0).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **int** che indica il tipo di SQLSTATE. Può essere uno dei valori seguenti:  
  
-   Per Java Runtime Environment versione 5.0: se il **xopenStates** proprietà di connessione è impostata su **true**, questo metodo restituisce DatabaseMetaData.sqlStateXOpen. In caso contrario, DatabaseMetaData.sqlStateSQL99.  
  
-   Per Java Runtime Environment versione 6.0: se il **xopenStates** proprietà di connessione è impostata su **true**, questo metodo restituisce DatabaseMetaData.sqlStateXOpen. In caso contrario, DatabaseMetaData.sqlStateSQL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getSQLStateType viene specificato dal metodo getSQLStateType nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
