---
title: Metodo (lang) prepareCall | Documenti Microsoft
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
- SQLServerConnection.prepareCall (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cb83b567-4ce5-447a-93cc-895d4eaf3a05
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e34bcabaf1ad68679454ad70308c187deecd325b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="preparecall-method-javalangstring"></a>Metodo prepareCall (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md) oggetto per la chiamata di stored procedure del database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.CallableStatement prepareCall(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Oggetto **stringa** contenente un'istruzione SQL.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto CallableStatement.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo prepareCall viene specificato dal metodo prepareCall nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo prepareCall &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
