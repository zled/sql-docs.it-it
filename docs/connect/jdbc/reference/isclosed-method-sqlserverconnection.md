---
title: Metodo (SQLServerConnection) isClosed | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerConnection.isClosed
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 634a402f06005c7235755988adf1435d38da0313
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="isclosed-method-sqlserverconnection"></a>isClosed (metodo) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto è stato chiuso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la connessione è chiusa, **false** in caso contrario.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo isClosed viene specificato dal metodo isClosed nell'interfaccia Java.SQL. Connection.  
  
 Verifica lo stato dell'oggetto SQLServerConnection chiamato. Una connessione viene chiusa se il [chiudere](../../../connect/jdbc/reference/close-method-sqlserverconnection.md) metodo è stato chiamato su di esso, o se si sono verificati alcuni errori irreversibili. Questo metodo restituirà **true** solo quando viene chiamato dopo la chiamata del metodo close.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
