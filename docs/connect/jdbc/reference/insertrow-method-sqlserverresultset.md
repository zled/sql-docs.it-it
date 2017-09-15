---
title: insertRow (metodo) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.insertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 363d1008-1396-4fc0-8e27-c9ba2499e7f1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9297b57b1ad4ded2611fadb1034a61046e3a4d25
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="insertrow-method-sqlserverresultset"></a>insertRow (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiunge il contenuto della riga di inserimento a questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto e al database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void insertRow()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo insertRow viene specificato dal metodo insertRow nell'interfaccia Java.SQL. ResultSet.  
  
 Il cursore deve trovarsi sulla riga di inserimento quando viene effettuata la chiamata a questo metodo. Una volta chiamato il metodo, il cursore rimane sulla riga di inserimento e il set di risultati rimane in modalità di inserimento.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
