---
title: rowUpdated (metodo) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.rowUpdated
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 29303550-294e-4d43-b892-312b42e21271
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5f9b34859431b995ddfe6788b6eb08d6d9ed9d74
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="rowupdated-method-sqlserverresultset"></a>rowUpdated (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera informazioni sull'eventuale aggiornamento della riga corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean rowUpdated()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la riga è stata aggiornata visibilmente dal proprietario o un altro utente e vengono rilevati gli aggiornamenti. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo rowUpdated viene specificato dal metodo rowUpdated nell'interfaccia Java.SQL. ResultSet.  
  
 Il valore restituito dipende dall'eventuale rilevamento degli aggiornamenti da parte del set di risultati.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]non rileva le righe aggiornate per qualsiasi tipo di cursore.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

