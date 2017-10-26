---
title: Metodo getResponseBuffering (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a7d17eb34ef5acdeea9870d1b330423c015bf23a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
  
 **completa** specifica lettura dell'intero risultato dal server in fase di esecuzione.  
  
 **adattivo** è il valore predefinito nel Driver JDBC versione 2.0 e 3.0. **completa** è l'impostazione predefinita, prima del Driver JDBC versione 2.0.  
  
 Per ulteriori informazioni sull'utilizzo della modalità di buffering di risposta, vedere [utilizzando il buffer adattivo](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setResponseBuffering &#40; SQLServerStatement &#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

