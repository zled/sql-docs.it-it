---
title: Metodo isFirst (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isFirst
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ff94b95-32ad-4378-8bb1-970030527bb2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eba9be492a28d3254b0f8826a4cdf2c566ae285f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795799"
---
# <a name="isfirst-method-sqlserverresultset"></a>Metodo isFirst (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera informazioni circa l'eventuale presenza del cursore nella prima riga di questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isFirst()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il cursore si trova nella prima riga. **false** se il cursore si trova in qualsiasi altra posizione oppure se il set di risultati non contiene righe.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo isFirst è specificato dal metodo isFirst nell'interfaccia ResultSet.  
  
 Se questo metodo viene utilizzato con i cursori forward e dinamici, viene generata un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
