---
title: Metodo (lang) (SQLServerResultSet) getByte | Documenti Microsoft
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
- SQLServerResultSet.getByte (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 069c68ff-442d-4104-917f-3445a3ad264a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 24f47eabe5f89dc7cdbb419dffe44cb4af21bd36
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getbyte-method-javalangstring-sqlserverresultset"></a>getByte (metodo) (lang) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del nome della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **byte** nel linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public byte getByte(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **byte** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getByte viene specificato dal metodo getByte nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo è supportato solo in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipi di dati che possono restituire in modo sicuro un valore di byte, ad esempio tinyint e bit. Tutti gli altri tipi di dati genereranno un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getByte &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbyte-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
