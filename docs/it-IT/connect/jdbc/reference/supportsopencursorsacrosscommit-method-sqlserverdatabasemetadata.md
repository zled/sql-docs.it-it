---
title: Metodo supportsOpenCursorsAcrossCommit | Documenti Microsoft
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
- SQLServerDatabaseMetaData.supportsOpenCursorsAcrossCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b7eed108-64cc-4be6-b297-8af6c1e3dc72
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d8a5db9298e5b5e17f8294af43c939ddcd19d469
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supportsopencursorsacrosscommit-method-sqlserverdatabasemetadata"></a>Metodo supportsOpenCursorsAcrossCommit (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database consente di mantenere i cursori aperti tra i vari commit.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsOpenCursorsAcrossCommit()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo supportsOpenCursorsAcrossCommit viene specificato dal metodo supportsOpenCursorsAcrossCommit nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
