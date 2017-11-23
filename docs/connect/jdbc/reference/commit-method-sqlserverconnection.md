---
title: Commit (metodo) (SQLServerConnection) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerConnection.commit
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: c7346165-51bf-4844-b64c-29833c147236
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d99a568ebff4f97fead61019430b5f5c176deef
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="commit-method-sqlserverconnection"></a>Commit (metodo) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rende tutte permanenti le modifiche apportate dopo il commit o rollback precedente e rilascia eventuali blocchi del database attualmente mantenuti attivi da questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void commit()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo commit viene specificato dal metodo nell'interfaccia Java.SQL. Connection commit.  
  
 Questo metodo deve essere utilizzato solo quando la modalità autocommit è stata disabilitata.  
  
 Si noti che questo metodo avrà esito negativo e genererà un'eccezione se il client avvia una transazione manuale e se successivamente, per qualche motivo, SQL Server esegue il rollback della transazione manuale. Ad esempio, viene generata un'eccezione se il client chiama una stored procedure che chiama in modo esplicito il rollback della transazione e quindi il client chiama il metodo commit. Inoltre, se SQL Server genera un errore di gravità è sufficiente (16 o versione successiva) per eseguire il rollback il client avviata transazione manuale. una chiamata successiva al metodo commit genererà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
