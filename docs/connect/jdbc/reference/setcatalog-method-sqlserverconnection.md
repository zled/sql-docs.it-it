---
title: Metodo setCatalog (SQLServerConnection) | Documenti Microsoft
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
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b766c76132bad3f66de98b431ee09d39753c40ab
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setcatalog-method-sqlserverconnection"></a>Metodo setCatalog (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il nome di catalogo specificato per selezionare uno spazio secondario di questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) database dell'oggetto da utilizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalogo*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setCatalog viene specificato dal metodo setCatalog nell'interfaccia Java.SQL. Connection.  
  
 Il *catalogo* argomento di escape per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] automaticamente. Questo metodo imposta la proprietà di catalogo per l'oggetto connessione. Tale proprietà non viene impostata in modo implicito in altro modo.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

