---
title: Metodo (SQLServerConnection) setDisableStatementPooling | Documenti Microsoft
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
apiname:
- SQLServerConnection.setDisableStatementPooling
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26f77ed870a5c1bbc434573253c63148fae2f21f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setdisablestatementpooling-method-sqlserverconnection"></a>setDisableStatementPooling metodo (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Imposta il pool di istruzione su true o false. Se false, consente l'istruzione pool da utilizzare in accoppiamento con statementPoolingCacheSize valore > 0.

## <a name="syntax"></a>Sintassi  
  
```  
  
public void setDisableStatementPooling(boolean disableStatementPooling)  
```  

#### <a name="parameters"></a>Parametri  
 *disableStatementPooling*  
  
 Il nuovo valore della **disableStatementPooling** proprietà di connessione.  
 
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Osservazioni  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e successivo.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
