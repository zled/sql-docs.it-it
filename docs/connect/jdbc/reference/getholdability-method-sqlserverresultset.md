---
title: Metodo getHoldability (SQLServerResultSet) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4508d90f-c3c4-4eac-8001-fb0b93b66734
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae5a5d40381cd6b7939e7e67b5950e3d0e3644d3
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getholdability-method-sqlserverresultset"></a>Metodo getHoldability (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la trattenibilità [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** valore contenente uno dei livelli di trattenibilità seguenti:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getHoldability viene specificato dal metodo getHoldability nell'interfaccia Java.SQL. ResultSet.  
  
 Per impostare la trattenibilità del set di risultati, le applicazioni possono utilizzare il [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) classe. Dopo il [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) metodo viene chiamato e l'oggetto istruzione e il relativo oggetto set di risultati vengono creati e l'istruzione viene eseguita, l'applicazione potrebbe essere necessario modificare nuovamente la trattenibilità.  
  
 Per i cursori sul lato server, se connessi a SQL Server 2005 o versioni successive, l'impostazione influisce solo sulla trattenibilità dei nuovi set di risultati ancora da creare in tale connessione. In SQL Server 2000, tuttavia, l'impostazione influisce sulla trattenibilità sia dei set di risultati esistenti che in quelli nuovi ancora da creare in tale connessione.  
  
 Quando viene reimpostata la trattenibilità e viene chiamato il metodo getHoldability su oggetto del set di risultati creati in precedenza, il valore restituito da questo metodo può essere diverso dal valore di trattenibilità restituito dai metodi seguenti: Statement.getResultSetHoldability , Connection.getHoldability o DatabaseMetaData.getResultSetHoldability.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
