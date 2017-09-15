---
title: Metodo (lang) getSQLXML | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f56b192a-3255-4215-b552-8e494fbca083
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 21eba6572ba201ae68891cf2c80545d586903290
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getsqlxml-method-javalangstring"></a>Metodo getSQLXML (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro designato come oggetto SQLXML in base al nome del parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterName*  
  
 Oggetto **stringa** che indica il nome del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 ASQLXMLobject.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getSQLXML viene specificato dal metodo getSQLXML nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getSQLXML &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
