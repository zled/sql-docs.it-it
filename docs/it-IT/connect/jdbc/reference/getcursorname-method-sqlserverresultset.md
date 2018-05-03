---
title: Metodo getCursorName (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.getCursorName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e5b3af67-423a-4551-a4c6-a4bc076bd504
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9380759edeb222776f9686c56192b6d1a877ad23
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getcursorname-method-sqlserverresultset"></a>Metodo getCursorName (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il nome del cursore SQL utilizzato da questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
> [!NOTE]  
>  Questo metodo non è attualmente supportato per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Se viene chiamato, verrà generata un'eccezione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getCursorName()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il nome del cursore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getCursorName viene specificato dal metodo getCursorName nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
