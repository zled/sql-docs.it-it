---
title: Metodo isCatalogAtStart (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.isCatalogAtStart
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 665173d2-14c7-4ce1-954e-4adb53fb9b39
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5e5f6211831e8c8b343b65814ce59848b3a1875e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="iscatalogatstart-method-sqlserverdatabasemetadata"></a>Metodo isCatalogAtStart (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se un catalogo viene visualizzato all'inizio di un nome di tabella completo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isCatalogAtStart()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il nome del catalogo è il primo. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo isCatalogAtStart viene specificato dal metodo isCatalogAtStart nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
