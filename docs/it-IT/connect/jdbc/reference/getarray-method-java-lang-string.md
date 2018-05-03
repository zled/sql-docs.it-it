---
title: metodo getArray (metodo) (lang) | Documenti Microsoft
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
- SQLServerCallableStatement.getArray (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4610cbaf-5638-4a66-bd83-70aefca40e58
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ede8fed980a47c298dd6cd64633aed91f326fd4e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getarray-method-javalangstring"></a>Metodo getArray (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro designato come oggetto matrice in base al nome del parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Array getArray(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sCol*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto matrice.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getArray viene specificato dal metodo getArray nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getArray &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getarray-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
