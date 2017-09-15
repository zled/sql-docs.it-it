---
title: Metodo supportsAlterTableWithDropColumn | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.supportsAlterTableWithDropColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 55a182c1-28e5-4d32-aeb1-166a8ac76758
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c7138410182d373a91f06358912aa27e42e37072
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="supportsaltertablewithdropcolumn-method-sqlserverdatabasemetadata"></a>Metodo supportsAlterTableWithDropColumn (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database supporta ALTER TABLE con eliminazione di colonne.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsAlterTableWithDropColumn()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo supportsAlterTableWithDropColumn viene specificato dal metodo supportsAlterTableWithDropColumn nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
