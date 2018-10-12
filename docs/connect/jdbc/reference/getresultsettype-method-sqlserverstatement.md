---
title: Metodo getResultSetType (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResultSetType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 260da35f-ddf6-4111-8519-69956ea3072e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 336b9844a13ae375eb6ae921bc4ea24b72d474ac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798265"
---
# <a name="getresultsettype-method-sqlserverstatement"></a>Metodo getResultSetType (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il tipo di set di risultati per gli oggetti [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) generati da questo oggetto [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final int getResultSetType()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **int** che indica il tipo di set di risultati.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getResultSetType viene specificato dal metodo getResultSetType nell'interfaccia Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
