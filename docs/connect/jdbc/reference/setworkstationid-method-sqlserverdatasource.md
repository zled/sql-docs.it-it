---
title: Metodo setWorkstationID (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.setWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c1093615-90bf-4918-9f05-8abd765ffb03
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 536a0b9dd7f047ae725bb03c45a5e3d8357a8f90
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setworkstationid-method-sqlserverdatasource"></a>Metodo setWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il nome del computer client utilizzato per la connessione all'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setWorkstationID(java.lang.String workstationID)  
```  
  
#### <a name="parameters"></a>Parametri  
 *oggetto workstationID*  
  
 Oggetto **stringa** che contiene il nome del computer client.  
  
## <a name="remarks"></a>Osservazioni  
 L'oggetto workstationID è il nome del computer o della workstation client. Se la proprietà workstationID non è impostata, il valore predefinito viene costruito chiamando il metodo InetAddress.getLocalHost().getHostName(). Se getHostName restituisce un valore vuoto, viene chiamato il metodo getHostAddress().toString().  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

