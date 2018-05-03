---
title: updateDateTimeOffset(int) (SQLServerResultSet) | Documenti Microsoft
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
ms.assetid: 21ec0054-c808-4e88-9c8d-c71b696ce658
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb7608fa2f22ef1faed895a97deb09b36329299c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="updatedatetimeoffsetint-microsoftsqldatetimeoffset-sqlserverresultset"></a>updateDateTimeOffset(int, microsoft.sql.DateTimeOffset) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0.  
  
 Aggiorna il valore della colonna specificata per il [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore, se un numero ordinale di colonna in base zero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Numero ordinale in base zero di una colonna.  
  
 *x*  
  
 Oggetto [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 È possibile recuperare un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore con [Getdatetimeoffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md).  
  
## <a name="see-also"></a>Vedere anche  
 [updateDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
