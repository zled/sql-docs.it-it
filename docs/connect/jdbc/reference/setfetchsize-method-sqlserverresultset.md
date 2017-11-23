---
title: Metodo (SQLServerResultSet) setFetchSize | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.setFetchSize
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 233bf4f8-4758-42d0-a80b-33e34fa78027
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a143006cbd2a5482bd919b4e2cd648d91290291d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="setfetchsize-method-sqlserverresultset"></a>setFetchSize (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fornisce al driver JDBC un hint per il numero di righe che devono essere recuperate dal database quando sono necessarie più righe per questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Parametri  
 *righe*  
  
 Un **int** che indica il numero di righe da recuperare.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setFetchSize viene specificato dal metodo setFetchSize nell'interfaccia Java.SQL. ResultSet.  
  
 Se la dimensione di recupero specificata è pari a zero, il driver JDBC ignora il valore e valuta la dimensione necessaria. Il valore predefinito è impostato il [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto che ha creato il set di risultati. È possibile modificare la dimensione di recupero in qualunque momento.  
  
 Questo metodo modifica la dimensione di recupero del blocco per i cursori server e viene applicato alla successiva chiamata al metodo sp_cursorfetch da parte del driver JDBC. L'impostazione della dimensione di recupero su zero ripristina la dimensione di recupero predefinita per il tipo di cursore attualmente utilizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
