---
title: Metodo isDefinitelyWritable (SQLServerResultSetMetaData) | Documenti Microsoft
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
- SQLServerResultSetMetaData.isDefinitelyWritable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7650e89a-dc8e-43ca-8eb2-f962f1a4b4ae
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efd52a613717347abbfd3d3092bc860834f79493
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="isdefinitelywritable-method-sqlserverresultsetmetadata"></a>Metodo isDefinitelyWritable (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se un'operazione di scrittura nella colonna designata riuscirà sicuramente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isDefinitelyWritable(int column)  
```  
  
#### <a name="parameters"></a>Parametri  
 *column*  
  
 Un **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la scrittura nella colonna riesce. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo isDefinitelyWritable viene specificato dal metodo isDefinitelyWritable nell'interfaccia Java.SQL. ResultSetMetaData.  
  
> [!NOTE]  
>  Quando si utilizza il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] con un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database, questo metodo restituirà sempre false.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membri di SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Classe SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
