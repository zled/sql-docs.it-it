---
title: Metodo updateTimestamp (int, java.sql.Timestamp) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateTimestamp (int, java.sql.Timestamp)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db83d9d7-137b-4a28-a2ca-d4782e0a256e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 287f5a80d02336df0d78a479f35c51fda8c8f37e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811529"
---
# <a name="updatetimestamp-method-int-javasqltimestamp"></a>Metodo updateTimestamp (int, java.sql.Timestamp)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la colonna designata con un valore di timestamp in base all'indice di colonna.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateTimestamp(int index,  
                            java.sql.Timestamp x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Valore **int** che indica l'indice di colonna.  
  
 *x*  
  
 Valore di timestamp.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo updateTimestamp viene specificato dal metodo updateTimestamp nell'interfaccia ResultSet.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo updateTimestamp &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
