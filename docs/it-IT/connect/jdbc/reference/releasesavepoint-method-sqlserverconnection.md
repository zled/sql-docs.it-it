---
title: Metodo releaseSavepoint (SQLServerConnection) | Documenti Microsoft
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
- SQLServerConnection.releaseSavepoint
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b6b625ea-c7ce-4a32-a9e0-6d2b4321bfd8
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b816e17f3b1d6ee4d7711b4ae3548acdc2475403
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="releasesavepoint-method-sqlserverconnection"></a>Metodo releaseSavepoint (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rimuove il determinato [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) oggetto dalla transazione corrente.  
  
> [!NOTE]  
>  Questo metodo non è attualmente supportato per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void releaseSavepoint(java.sql.Savepoint savepoint)  
```  
  
#### <a name="parameters"></a>Parametri  
 *punto di salvataggio*  
  
 L'oggetto punto di salvataggio da rimuovere.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo releaseSavepoint viene specificato dal metodo releaseSavepoint nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
