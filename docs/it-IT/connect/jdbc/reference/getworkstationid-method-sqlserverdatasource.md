---
title: Metodo getWorkstationID (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.getWorkstationID
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6a701de-a8fa-4668-9310-99a8c6e32c88
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6145e5ef7213be282f556f93d3b342c19109c705
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getworkstationid-method-sqlserverdatasource"></a>Metodo getWorkstationID (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il nome del computer client utilizzato per la connessione all'origine dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getWorkstationID()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il nome del computer client.  
  
## <a name="remarks"></a>Osservazioni  
 L'oggetto workstationID è il nome del computer o della workstation client. Se la proprietà workstationID non è impostata, il valore predefinito viene costruito chiamando il metodo InetAddress.getLocalHost().getHostName(). Se getHostName restituisce un valore vuoto, viene chiamato il metodo getHostAddress().toString().  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
