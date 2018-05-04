---
title: Metodo setFetchDirection (SQLServerResultSet) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c1f042804aa21ca91031c56d285bbfb9d0d8e1f0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setfetchdirection-method-sqlserverresultset"></a>Metodo setFetchDirection (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fornisce un hint per la direzione in cui le righe in questa [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto verrà elaborato.  
  
> [!NOTE]  
>  Questo metodo non è attualmente supportato per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Se si utilizza questo metodo, nel driver JDBC l'impostazione viene memorizzata, ma non viene utilizzata per effettuare operazioni.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Direzione*  
  
 Un **int** che indica la direzione di recupero suggerita. I possibili valori sono i seguenti:  
  
 ResultSet.FETCH_FORWARD  
  
 ResultSet.FETCH_REVERSE  
  
 ResultSet.FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setFetchDirection viene specificato dal metodo setFetchDirection nell'interfaccia Java.SQL. ResultSet.  
  
 Il valore iniziale di questo metodo è determinato dal [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto che ha generato questo oggetto SQLServerResultSet. È possibile modificare la direzione di recupero in qualunque momento.  
  
> [!NOTE]  
>  L'utilizzo di questo metodo quando il tipo di cursore è forward only non ha effetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
