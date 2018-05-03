---
title: Metodo nativeSQL (SQLServerConnection) | Documenti Microsoft
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
- SQLServerConnection.nativeSQL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2188a6e1-792f-47bd-b207-1d01741231b2
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0f7c55a61d440e3991f74388c9a96be09430f2c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="nativesql-method-sqlserverconnection"></a>Metodo nativeSQL (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Converte l'istruzione SQL specificata nella grammatica SQL nativa del server di database.  
  
> [!NOTE]  
>  Questo metodo non è attualmente supportato per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String nativeSQL(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Oggetto **stringa** contenente un'istruzione SQL.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** contenente l'istruzione SQL convertita.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo nativeSQL viene specificato dal metodo nativeSQL nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
