---
title: Metodo al tipo registerOutParameter | Documenti Microsoft
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
- SQLServerCallableStatement.registerOutParameter (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d00242c-4d9c-42cc-86bb-b76f5ef876b8
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf75d2aca5dc8b5373a84f84bf70734fcb7cc494
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="registeroutparameter-method-javalangstring-int"></a>Metodo registerOutParameter (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Registra il parametro OUT con il nome specificato nel tipo JDBC fornito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n)  
```  
  
#### <a name="parameters"></a>Parametri  
 *S*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
 *n*  
  
 Codice di tipo JDBC come definito in java.sql.Types.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo registerOutParameter viene specificato dal metodo registerOutParameter nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo registerOutParameter &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
