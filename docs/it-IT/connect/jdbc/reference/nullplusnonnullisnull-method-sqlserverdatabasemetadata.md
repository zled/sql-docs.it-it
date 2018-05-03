---
title: Metodo nullPlusNonNullIsNull (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.nullPlusNonNullIsNull
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c594736f-3a9b-463f-bbd8-eaf9221230ea
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2296ac9d131ebd3f7530606a4d00351378f773c1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="nullplusnonnullisnull-method-sqlserverdatabasemetadata"></a>Metodo nullPlusNonNullIsNull (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se il database supporta concatenazioni tra valori NULL e non NULL che sono NULL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean nullPlusNonNullIsNull()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se le concatenazioni sono supportate. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo nullPlusNonNullIsNull viene specificato dal metodo nullPlusNonNullIsNull nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
