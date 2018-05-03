---
title: Metodo (lang) (SQLServerStatement) executeUpdate | Documenti Microsoft
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
- SQLServerStatement.executeUpdate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85e7c3a2-f2da-49bf-9d90-5fd246fd60e1
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e5a05bc78ec035352c7784ecdb5a24da89d354b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="executeupdate-method-javalangstring-sqlserverstatement"></a>Metodo executeUpdate (java.lang.String) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esegue l'istruzione SQL specificata, che può essere un'istruzione INSERT, UPDATE o DELETE, oppure un'istruzione SQL che non restituisce nulla, ad esempio un'istruzione SQL DDL. A partire da [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0, il metodo executeUpdate restituirà il numero corretto di righe aggiornate in un'operazione di unione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int executeUpdate(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Oggetto **stringa** che contiene l'istruzione SQL.  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il numero di righe interessate oppure 0 se si utilizza un'istruzione DDL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo executeUpdate viene specificato dal metodo executeUpdate nell'interfaccia Java.SQL. Statement.  
  
 Se l'esecuzione di una stored procedure restituisce un conteggio di aggiornamento che è maggiore di uno o genera più set di risultati, utilizzare il [eseguire](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) metodo per eseguire la stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo executeUpdate &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
