---
title: insertRow (metodo) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.insertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 363d1008-1396-4fc0-8e27-c9ba2499e7f1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eafc73e9a5a5179992cec3d042f82ac460ee2bd3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
  
  
