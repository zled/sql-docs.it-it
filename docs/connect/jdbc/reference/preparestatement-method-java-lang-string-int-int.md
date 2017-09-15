---
title: Metodo prepareStatement (lang, int, int) | Documenti Microsoft
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
- SQLServerConnection.prepareStatement (java.lang.String, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5bb96dbe-f673-41b5-911b-8f661cca071a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cf94fb0b8d641e024e4c4a448694a595c3169d77
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="preparestatement-method-javalangstring-int-int"></a>Metodo prepareStatement (java.lang.String, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) oggetto che genera l'errore [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetti con il tipo specificato e la concorrenza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sSql,  
                                                   int resultSetType,  
                                                   int resultSetConcurrency)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sSql*  
  
 Oggetto **stringa** contenente un'istruzione SQL.  
  
 *resultSetType*  
  
 Un **int** che indica il set di risultati tipo.  
  
 *resultSetConcurrency*  
  
 Un **int** che indica il tipo di concorrenza del set di risultati.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto PreparedStatement.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo prepareStatement viene specificato dal metodo prepareStatement nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-methods.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
