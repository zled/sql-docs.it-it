---
title: Metodo updatesAreDetected (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.updatesAreDetected
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cb541175-d3a5-4bca-b327-64e2270c0df1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 080a44ecd1925cbb42cdddf0496766705fa06119
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updatesaredetected-method-sqlserverdatabasemetadata"></a>Metodo updatesAreDetected (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera o meno in cui è possibile rilevare un aggiornamento di riga visibile chiamando il [rowUpdated](../../../connect/jdbc/reference/rowupdated-method-sqlserverresultset.md) metodo il [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) classe.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean updatesAreDetected(int type)  
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
  
## <a name="return-value"></a>Valore restituito  
 **true** se è possibile rilevare l'aggiornamento della riga. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo updatesAreDetected viene specificato dal metodo updatesAreDetected nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
