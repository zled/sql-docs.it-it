---
title: Metodo setResponseBuffering (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c5af0e179ea15fc4d5a30604b606f5ff45c79a1b
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>Metodo setResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta la risposta per questa modalità di buffering [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto distinzione **stringa completa** o **adattivo**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Valore*  
  
 Oggetto **stringa** che contiene la modalità di buffer di risposta. La modalità valida può essere una delle seguenti stringhe tra maiuscole e minuscole: **completo** o **adattivo**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 **adattivo** specifica il buffer di dati minima possibile quando necessario.  
  
 **completa** specifica lettura dell'intero risultato dal server in fase di esecuzione.  
  
 Adaptive è il valore predefinito nel Driver JDBC versione 2.0 e 3.0. full è il valore predefinito prima di Driver JDBC versione 2.0.  
  
 Il [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) metodo consente di eseguire l'override di **responseBuffering** connessione **stringa** proprietà per l'oggetto corrente [ SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto. Per ulteriori informazioni sull'utilizzo della modalità di buffering di risposta, vedere [utilizzando il buffer adattivo](../../../connect/jdbc/using-adaptive-buffering.md).  
  
 Se l'applicazione specifica un valore di parametro non valido per il [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) (metodo), un [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) viene generata un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [Utilizzo del buffer adattivo](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  

