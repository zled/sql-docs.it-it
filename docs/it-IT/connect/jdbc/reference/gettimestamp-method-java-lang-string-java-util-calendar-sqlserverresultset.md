---
title: Metodo getTimestamp (lang, java.util.Calendar) | Documenti Microsoft
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
- SQLServerResultSet.getTimestamp (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 44474000-8951-49ee-93a5-c8cb879eaf55
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb5ec1a44b0be2afa42191592c3315d9e0fe00a3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="gettimestamp-method-javalangstring-javautilcalendar-sqlserverresultset"></a>Metodo getTimestamp (lang, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del nome della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come oggetto java.SQL. timestamp nel linguaggio linguaggio di programmazione, utilizzando un oggetto di calendario.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Timestamp getTimestamp(java.lang.String colName,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ColName*  
  
 Oggetto **stringa** che contiene il nome della colonna.  
  
 *licenza CAL*  
  
 Un oggetto di calendario.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto di tipo Timestamp.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getTimestamp viene specificato dal metodo getTimestamp nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo restituisce valori solo dalle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] colonne datetime e smalldatetime.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getTimestamp &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
