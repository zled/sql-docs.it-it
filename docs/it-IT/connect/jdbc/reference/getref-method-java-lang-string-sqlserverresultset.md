---
title: Metodo (lang) (SQLServerResultSet) getRef | Documenti Microsoft
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
- SQLServerResultSet.getRef (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 83c60c5d-7a69-498b-be9c-bbdbfafec157
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8852dcfb6efeef5723e9472a03158859c3a91f2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getref-method-javalangstring-sqlserverresultset"></a>getRef (metodo) (lang) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del nome della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto di riferimento nel linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Ref getRef(java.lang.String colName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ColName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto di riferimento.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getRef viene specificato dal metodo getRef nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getRef &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getref-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
