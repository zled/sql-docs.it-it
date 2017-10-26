---
title: Metodo getDateTimeOffset (String) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fedb1d75-0c3d-4eb3-ae65-da0e153265cc
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 08a70615c065d2b5f981a0e57231a437b00f925e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getdatetimeoffset-method-string"></a>Metodo getDateTimeOffset (String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0.  
  
 Recupera il valore del parametro designato come un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) oggetto in base all'indice del parametro di linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(String sCol)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCol*  
  
 Nome di un parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) oggetto.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 È possibile impostare un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) valore del parametro con [Setdatetimeoffset](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getDateTimeOffset &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

