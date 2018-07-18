---
title: I membri di SQLServerXAConnection | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4b61dabd-369b-460c-8450-9fe424f76541
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 188140965c0040f8454156555b71adbd2fe89ce9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851066"
---
# <a name="sqlserverxaconnection-members"></a>Membri di SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Le tabelle seguenti elencano i membri esposti dal [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) classe.  
  
## <a name="constructors"></a>Costruttori  
 Nessuno  
  
## <a name="fields"></a>Campi  
 Nessuno  
  
## <a name="inherited-fields"></a>Campi ereditati  
 Nessuno  
  
## <a name="methods"></a>Metodi  
  
|Nome|Description|  
|----------|-----------------|  
|[addConnectionEventListener](../../../connect/jdbc/reference/addconnectioneventlistener-method-sqlserverpooledconnection.md)|(Ereditato da [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) registra il listener di eventi specificato in modo che verrà notificato quando si verifica un evento su questo oggetto di connessione.|  
|[Chiudere](../../../connect/jdbc/reference/close-method-sqlserverpooledconnection.md)|(Ereditato da [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) chiude la connessione fisica rappresentata da questo oggetto di connessione.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverpooledconnection.md)|(Ereditato da [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) crea un handle di oggetto per la connessione fisica rappresentata da questo oggetto di connessione.|  
|[getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)|Recupera un [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) che il gestore delle transazioni verrà utilizzato per gestire la partecipazione di questo [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) oggetto in una transazione distribuita.|  
|[removeConnectionEventListener](../../../connect/jdbc/reference/removeconnectioneventlistener-method-sqlserverpooledconnection.md)|(Ereditato da [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) consente di rimuovere il listener di eventi specificato.|  
  
## <a name="inherited-methods"></a>Metodi ereditati  
  
|Classe ereditata da:|Metodi|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|javax.sql.PooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
  
## <a name="see-also"></a>Vedere anche  
 [Classe SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
