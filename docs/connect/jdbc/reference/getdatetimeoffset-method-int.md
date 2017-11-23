---
title: Metodo getDateTimeOffset (int) | Documenti Microsoft
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
ms.assetid: 8bb00356-4d6e-4625-b924-67646930fdf2
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 019000c882372e7a80ead2761d2e207738a25f72
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="getdatetimeoffset-method-int"></a>Metodo getDateTimeOffset (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0.  
  
 Recupera il valore del parametro designato come un [classe DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) oggetto in base all'indice del parametro di linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(int index)  
```  
  
#### <a name="parameters"></a>Parametri  
 *indice*  
  
 Numero ordinale del parametro in base uno.  
  
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
  
  
