---
title: Metodo getFetchDirection (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ae039ccdc76cdc6117f502971feafe683f58b0d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getfetchdirection-method-sqlserverstatement"></a>Metodo getFetchDirection (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la direzione per il recupero delle righe dalle tabelle di database che è il valore predefinito per i set di risultati generati da questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.  
  
> [!NOTE]  
>  Questo metodo non è attualmente implementato dal [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Verrà pertanto sempre restituito FETCH_UNKNOWN.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final int getFetchDirection()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica la direzione di recupero specificato per il [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md) metodo.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getFetchDirection viene specificato dal metodo getFetchDirection nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
