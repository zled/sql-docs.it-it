---
title: Metodo Execute () | Documenti Microsoft
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
- SQLServerPreparedStatement.execute ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fa96d0f8-101b-422f-a767-405be9a5f74f
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c71a891d9de7b8f11c983737bd710d8702b92c3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="execute-method-"></a>Metodo execute ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esegue l'istruzione SQL in questo [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) oggetto, che può essere qualsiasi tipo di istruzione SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean execute()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se l'istruzione restituisce un set di risultati. **false** se viene restituito un conteggio aggiornamenti o nessun risultato.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo execute viene specificato dal metodo execute nell'interfaccia Java.SQL. PreparedStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [eseguire il metodo &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
