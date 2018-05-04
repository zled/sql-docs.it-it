---
title: Interfaccia ISQLServerConnection | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 031c01e2-2c65-4fe4-9700-fdbcc7a39f30
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ca0e0504a7f28622ba2419545d2167ad917f784
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="isqlserverconnection-interface"></a>Interfaccia ISQLServerConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta una connessione JDBC a un [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database. Questa interfaccia è stata aggiunta in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** Java  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public interface ISQLServerConnection  
```  
  
## <a name="remarks"></a>Osservazioni  
 Questa interfaccia è implementata da [classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
 Questa interfaccia espone i seguenti [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-campo specifico:  
  
|Campo|Per ulteriori informazioni, vedere|  
|-----------|-------------------------------|  
|public final static int TRANSACTION_SNAPSHOT|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|  
|public UUID getClientConnectionId()|[getClientConnectionID()](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
