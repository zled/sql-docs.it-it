---
title: Metodo Truncate (SQLServerNClob) | Documenti Microsoft
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
ms.assetid: b7e8210d-a724-4bae-832a-ae4c63031c9c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 79372fc2d1318c015f252c4bd8a425ab3e749fbc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="truncate-method-sqlservernclob"></a>Metodo truncate (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tronca il **NCLOB** alla lunghezza specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Parametri  
 *len*  
  
 Lunghezza, espressa in caratteri, a cui il **NCLOB** valore deve essere troncato.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo truncato viene specificato dal metodo nell'interfaccia Java.SQL. NClob troncamento.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membri di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
