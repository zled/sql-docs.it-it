---
title: Metodo getUDTs (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getUDTs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4396453-dcb0-4132-8325-06b3c7896b3b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad46134dff0958dce446c282d3e9a26dc661e351
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getudts-method-sqlserverdatabasemetadata"></a>Metodo getUDTs (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera una descrizione dei tipi definiti dall'utente configurati in un determinato schema.  
  
> [!NOTE]  
>  Questo metodo non è attualmente supportato con [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Quando viene utilizzato questo metodo, viene restituito sempre un set di risultati vuoto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.ResultSet getUDTs(java.lang.String catalog,  
                                  java.lang.String schemaPattern,  
                                  java.lang.String typeNamePattern,  
                                  int[] types)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
 *schemaPattern*  
  
 Oggetto **stringa** che contiene il modello di nome dello schema.  
  
 *typeNamePattern*  
  
 Oggetto **stringa** che contiene il modello di nome di tipo.  
  
 *Tipi*  
  
 Una matrice di valori ints contenente i tipi di dati da includere. Null indica che devono essere inclusi tutti i tipi.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getUDTs viene specificato dal metodo getUDTs nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
