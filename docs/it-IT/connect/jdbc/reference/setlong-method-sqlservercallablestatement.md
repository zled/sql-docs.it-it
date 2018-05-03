---
title: Metodo setLong (SQLServerCallableStatement) | Documenti Microsoft
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
- SQLServerCallableStatement.setLong
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 137416fe-a580-424e-be79-fe946eba9e6e
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e788e2d175c24519abd0a8d18db787a6f35da172
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setlong-method-sqlservercallablestatement"></a>Metodo setLong (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato il dato **lungo** valore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setLong(java.lang.String sCol,  
                    long l)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCol*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
 *L*  
  
 Oggetto **lungo** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setLong viene specificato dal metodo setLong nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
