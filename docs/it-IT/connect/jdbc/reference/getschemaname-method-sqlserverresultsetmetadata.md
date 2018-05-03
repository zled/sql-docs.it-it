---
title: Metodo getSchemaName (SQLServerResultSetMetaData) | Documenti Microsoft
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
- SQLServerResultSetMetaData.getSchemaName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2d0063ab-d5d7-420f-b388-36d5169b1358
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd1dca2f5860e46cdc31ee2ba2852446ec4709f5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getschemaname-method-sqlserverresultsetmetadata"></a>Metodo getSchemaName (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ottiene il nome dello schema di tabella per la colonna designata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getSchemaName(int column)  
```  
  
#### <a name="parameters"></a>Parametri  
 *column*  
  
 Un **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il nome dello schema.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getSchemaName viene specificato dal metodo getSchemaName nell'interfaccia Java.SQL. ResultSetMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membri di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Classe SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
