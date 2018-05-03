---
title: Metodo getTimeDateFunctions (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getTimeDateFunctions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a56e08ae-6f4e-4dc6-b175-ff457d0d7a81
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: addd25adf09ec4135fd8f962c887fe563332fd7c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="gettimedatefunctions-method-sqlserverdatabasemetadata"></a>Metodo getTimeDateFunctions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un elenco delimitato da virgole delle funzioni data e ora disponibili con il database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getTimeDateFunctions()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene un elenco delle funzioni di data e ora.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getTimeDateFunctions viene specificato dal metodo getTimeDateFunctions nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
