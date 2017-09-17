---
title: Metodo (SQLServerConnection) setAutoCommit | Documenti Microsoft
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
- SQLServerConnection.setAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db1e22d2-e53f-474e-8c99-cb1fff7f491a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f1549693ac6b4e558c2fc86b29dc6aaa6122c235
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# setAutoCommit, metodo (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta la modalità autocommit per questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto allo stato specificato.  
  
## Sintassi  
  
```  
  
public void setAutoCommit(boolean value)  
```  
  
#### Parametri  
 *Valore*  
  
 **true** per attivare la modalità autocommit per la connessione, **false** per disabilitarlo.  
  
## Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## Osservazioni  
 Questo metodo setAutoCommit viene specificato dal metodo setAutoCommit nell'interfaccia Java.SQL. Connection.  
  
 Se una connessione è in modalità autocommit, tutte le relative istruzioni SQL vengono eseguite e sottoposte a commit come transazioni singole. In caso contrario, le istruzioni SQL vengono raggruppate in transazioni terminate da una chiamata al [commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md) metodo o [rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md) metodo. Per impostazione predefinita, le nuove connessioni sono in modalità autocommit.  
  
 Il commit si verifica quando l'istruzione viene completata o si verifica l'esecuzione successiva, indipendentemente dall'evento che avviene per primo. Nel caso di istruzioni che restituiscono un [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) dell'oggetto, l'istruzione viene completata quando è stata recuperata l'ultima riga del set di risultati o quando il set di risultati è stata chiusa. In casi avanzati, una singola istruzione potrebbe restituire più risultati oltre ai valori dei parametri di output. In queste circostanze, il commit si verifica quando sono stati recuperati tutti i risultati e i valori dei parametri di output.  
  
 Quando la modalità autocommit è **false**, il driver JDBC avvierà in modo implicito una nuova transazione dopo ciascun commit.  
  
> [!NOTE]  
>  Se questo metodo viene chiamato durante una transazione, quest'ultima viene sottoposta a commit.  
  
## Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
