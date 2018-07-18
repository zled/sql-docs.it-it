---
title: metodo getArray (metodo) (lang) (SQLServerResultSet) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getArray java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a98d159b-1fae-482a-9465-5411ce60f901
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1932f6e6d3909dcc3a526f3b6fa94c9c77deeb1a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32829256"
---
# <a name="getarray-method-javalangstring-sqlserverresultset"></a>metodo getArray (metodo) (lang) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del nome della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un oggetto matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Array getArray(java.lang.String colName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ColName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto matrice.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getArray viene specificato dal metodo getArray nell'interfaccia Java.SQL. ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getArray &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
