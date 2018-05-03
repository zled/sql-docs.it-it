---
title: Metodo (lang, long) (SQLServerNClob) Position | Documenti Microsoft
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
ms.assetid: 46d4beec-831a-449f-98b6-322a80cc499a
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a5b36a64645c99f03f83f4ee3b37000fae9a49d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="position-method-javalangstring-long-sqlservernclob"></a>Metodo position (java.lang.String, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la posizione del carattere in corrispondenza del quale la sottostringa specificata *searchstr* è presente il **NCLOB** valore rappresentato da questo **NClob** oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public long position(java.lang.String searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>Parametri  
 *searchstr*  
  
 Sottostringa da cercare.  
  
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
  
  
