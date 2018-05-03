---
title: Metodo supportsMultipleOpenResults (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.supportsMultipleOpenResults
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9480d280-5e3d-46ae-80e6-1bba3ac5a641
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ac00522e138653972d1009f933a67f6a9efe7623
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supportsmultipleopenresults-method-sqlserverdatabasemetadata"></a>Metodo supportsMultipleOpenResults (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Specifica se è possibile avere più [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) gli oggetti restituiti da una [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) oggetto contemporaneamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsMultipleOpenResults()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo supportsMultipleOpenResults viene specificato dal metodo supportsMultipleOpenResults nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
