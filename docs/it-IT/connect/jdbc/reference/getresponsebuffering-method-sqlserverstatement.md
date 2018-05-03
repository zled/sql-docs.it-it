---
title: Metodo getResponseBuffering (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c536c98a5d81a5ef9e6dfc7f5ef17c32e0ea7bb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getresponsebuffering-method-sqlserverstatement"></a>Metodo getResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la risposta per questa modalità di buffering [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** contenente minuscolo **completo** o **adattivo**.  
  
## <a name="remarks"></a>Osservazioni  
 **adattivo** specifica il buffer di dati minima possibile quando necessario.  
  
 **completa** specifica la lettura dell'intero risultato dal server in fase di esecuzione.  
  
 **adattivo** è il valore predefinito nel Driver JDBC versione 2.0 e 3.0. **completa** è il valore predefinito prima della versione 2.0 del Driver JDBC.  
  
 Per ulteriori informazioni sull'utilizzo della modalità di buffering di risposta, vedere [utilizzando il buffer adattivo](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setResponseBuffering &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
