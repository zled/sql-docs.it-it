---
title: Metodo (SQLServerPreparedStatement) setRef | Documenti Microsoft
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
- SQLServerPreparedStatement.setRef
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1a09bbf9-6f8f-4a21-85d2-2182111b5ce7
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e68bb9e5b6651728f5dd3380d8ec76ca8f4dc103
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setref-method-sqlserverpreparedstatement"></a>setRef (metodo) (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato sull'oggetto di riferimento specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setRef(int i,  
                         java.sql.Ref x)  
```  
  
#### <a name="parameters"></a>Parametri  
 *I*  
  
 Un **int** che indica il numero di parametro.  
  
 *x*  
  
 Un oggetto di riferimento.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setRef viene specificato dal metodo setRef nell'interfaccia Java.SQL. PreparedStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
