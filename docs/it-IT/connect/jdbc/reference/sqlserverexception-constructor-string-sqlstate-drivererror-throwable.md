---
title: Costruttore SQLServerException (lang, SQLState, DriverError, java.lang.Throwable) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
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
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c4726740d2768d3e32302946f86c00ac1390d23
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverexception-constructor-javalangstring-sqlstate-drivererror-javalangthrowable"></a>Costruttore SQLServerException (lang, SQLState, DriverError, java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Inizializza una nuova istanza di [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) classe quando viene specificato un **stringa** oggetto, un **sqlstate** oggetto, un **drivererror** oggetto e un **throwable** oggetto.

## <a name="syntax"></a>Sintassi  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState sqlState,
            DriverError driverError,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Parametri  
 *errText*  
  
 Stringa che contiene il testo dell'errore.
  
 *sqlState*  
  
 Un oggetto di enumerazione che contiene lo stato SQL.
 
 *driverError*  
  
 Un oggetto di enumerazione che contiene l'errore del driver.
 
 *cause*  
  
 Oggetto throwable che contiene la causa dell'eccezione.
  
## <a name="see-also"></a>Vedere anche  
 [Costruttori di SQLServerException](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [Membri di SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Classe SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
