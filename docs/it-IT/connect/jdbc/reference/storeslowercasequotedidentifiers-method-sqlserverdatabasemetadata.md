---
title: Metodo storesLowerCaseQuotedIdentifiers | Documenti Microsoft
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
- SQLServerDatabaseMetaData.storesLowerCaseQuotedIdentifiers
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3e104c9e-66d4-436b-8b5b-a00ff667c95b
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d414247a7c341e69e14c5a8efdb1d820db0742b1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="storeslowercasequotedidentifiers-method-sqlserverdatabasemetadata"></a>Metodo storesLowerCaseQuotedIdentifiers (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database non tiene conto della distinzione tra maiuscole e minuscole negli identificatori SQL con maiuscole e minuscole racchiusi tra virgolette e li archivia in minuscolo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean storesLowerCaseQuotedIdentifiers()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se gli identificatori vengono archiviati in minuscolo. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo storesLowerCaseQuotedIdentifiers viene specificato dal metodo storesLowerCaseQuotedIdentifiers nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
