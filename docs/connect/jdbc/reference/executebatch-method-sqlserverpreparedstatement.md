---
title: Metodo executeBatch (SQLServerPreparedStatement) | Documenti Microsoft
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
- SQLServerPreparedStatement.executeBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8418167e-cbd2-464d-b118-73cdd76080ed
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c339a53bd782047db67bc58a61283ce9cd4cbe9e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="executebatch-method-sqlserverpreparedstatement"></a>Metodo executeBatch (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Invia al database un batch di comandi da eseguire. Se tutti i comandi vengono eseguiti correttamente, restituisce una matrice di conteggi aggiornamenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int[] executeBatch()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Matrice di valori interi contenente i conteggi aggiornamenti.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
 java.sql.BatchUpdateException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo executeBatch viene specificato dal metodo executeBatch nell'interfaccia Java.SQL. Statement.  
  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 per è conforme all'indicazione JDBC 4.0, che una chiamata al metodo CallableStatement.executeBatch (ereditato da PreparedStatement) genererà un BatchUpdateException se la stored procedure accetta OUT o INOUT Restituisce un valore diverso da un conteggio aggiornamenti o dei parametri.  
  
 Questo metodo esegue l'override [executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

