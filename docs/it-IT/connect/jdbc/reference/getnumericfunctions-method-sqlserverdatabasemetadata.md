---
title: Metodo getNumericFunctions (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getNumericFunctions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8d1c3848-bdb7-452a-862f-6421e1a7ce8b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c1251389a7edbcd666aa3ab929584eca6450b40
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getnumericfunctions-method-sqlserverdatabasemetadata"></a>Metodo getNumericFunctions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un elenco delimitato da virgole delle funzioni matematiche disponibili con il database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getNumericFunctions()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene le funzioni matematiche disponibili.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getNumericFunctions viene specificato dal metodo getNumericFunctions nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
