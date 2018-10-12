---
title: Metodo deleteRow (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 466fa86609ba4f784e78ba9ac0fb5178d827645e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784119"
---
# <a name="deleterow-method-sqlserverresultset"></a>Metodo deleteRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Elimina la riga corrente da questo oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) e dal database sottostante.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void deleteRow()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo deleteRow viene specificato dal metodo deleteRow nell'interfaccia ResultSet.  
  
 Non è possibile chiamare questo metodo quando il cursore si trova sulla riga di inserimento.  
  
 In caso di utilizzo di cursori keyset, questo metodo lascia uno spazio vuoto nel set di risultati. È possibile verificare la presenza di questo spazio vuoto tramite il metodo [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md). I numeri delle righe del set di risultati non cambiano.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
