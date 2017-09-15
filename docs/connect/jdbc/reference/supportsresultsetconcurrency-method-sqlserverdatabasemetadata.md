---
title: Metodo supportsResultSetConcurrency (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.supportsResultSetConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8f7573b2-ac5c-4721-8a02-4b6cb60c74b2
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bba3f5a677884c20b5a960e558d6bbe3395fdff0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="supportsresultsetconcurrency-method-sqlserverdatabasemetadata"></a>Metodo supportsResultSetConcurrency (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database supporta il tipo di concorrenza specificato in combinazione con un dato tipo di set di risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsResultSetConcurrency(int type,  
                                            int concurrency)  
```  
  
#### <a name="parameters"></a>Parametri  
 *type*  
  
 Un **int** che indica il set di risultati tipo, che può essere uno dei valori seguenti come definito in Java.SQL. ResultSet o SQLServerResultSet:  
  
## <a name="javasqlresultset-types"></a>Tipi java.sql.ResultSet  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>Tipi SQLServerResultSet  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
 *concorrenza*  
  
 Un **int** che indica il set di risultati il livello di concorrenza, che può essere uno dei valori seguenti come definito in Java.SQL. ResultSet o SQLServerResultSet:  
  
## <a name="javasqlresultset-types"></a>Tipi java.sql.ResultSet  
 CONCUR_READ_ONLY  
  
 CONCUR_UPDATABLE  
  
## <a name="sqlserverresultset-types"></a>Tipi SQLServerResultSet  
 CONCUR_SS_OPTIMISTIC_CC  
  
 CONCUR_SS_SCROLL_LOCKS  
  
 CONCUR_SS_OPTIMISTIC_VAL  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo supportsResultSetConcurrency viene specificato dal metodo supportsResultSetConcurrency nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
