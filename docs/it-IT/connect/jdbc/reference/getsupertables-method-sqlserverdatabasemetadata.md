---
title: Metodo getSuperTables (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getSuperTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 085461de-367b-4832-88aa-010813d2bc41
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 355ad6db2533a7f4b15fb2bf23d613e9932b5c24
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getsupertables-method-sqlserverdatabasemetadata"></a>Metodo getSuperTables (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione delle gerarchie di tabelle definite in un determinato schema del database.  
  
> [!NOTE]  
>  Questo metodo non è attualmente supportato con la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Quando viene utilizzato questo metodo, viene restituito sempre un set di risultati vuoto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getSuperTables(java.lang.String catalog,  
                                         java.lang.String schemaPattern,  
                                         java.lang.String tableNamePattern)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
 *schemaPattern*  
  
 Oggetto **stringa** che contiene il modello di nome dello schema.  
  
 *tableNamePattern*  
  
 Oggetto **stringa** che contiene il modello di nome di tabella.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getSuperTables viene specificato dal metodo getSuperTables nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
