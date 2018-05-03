---
title: Position (Java.SQL. NClob, long) (metodo) | Documenti Microsoft
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
ms.assetid: f2354278-d128-4cf4-a170-22c05fcb763b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bcac66bf3ca49b7837d3b552d708cea16422de1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="position-method-javasqlnclob-long"></a>Metodo position (java.sql.NClob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la posizione del carattere in corrispondenza del quale l'oggetto specificato **NClob** oggetto *searchstr* viene visualizzato in questa **NClob** oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
long position(java.sql.NClob searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>Parametri  
 *searchstr*  
  
 Un oggetto NClob da cercare.  
  
 *start*  
  
 Posizione da cui iniziare la ricerca. La prima posizione è 1.  
  
## <a name="return-value"></a>Valore restituito  
 Posizione in cui viene visualizzata la sottostringa oppure -1 se non è presente. La prima posizione è 1.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo di posizione è specificato dal metodo nell'interfaccia Java.SQL. NClob posizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Position &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [Metodi di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membri di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
