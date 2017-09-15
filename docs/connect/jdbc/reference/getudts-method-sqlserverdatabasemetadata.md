---
title: Metodo getUDTs (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getUDTs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4396453-dcb0-4132-8325-06b3c7896b3b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5d15d63bbb6d39696664331d6eb29b225ac74d2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
 *catalogo*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
 *schemaPattern*  
  
 Oggetto **stringa** che contiene il modello di nome dello schema.  
  
 *typeNamePattern*  
  
 Oggetto **stringa** che contiene il modello di nome di tipo.  
  
 *tipi*  
  
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
  
  
