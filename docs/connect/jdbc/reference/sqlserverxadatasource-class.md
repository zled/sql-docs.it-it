---
title: Classe SQLServerXADataSource | Documenti Microsoft
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
ms.topic: article
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7745863cfa6ad05d5aefa85b865751fe3f11f392
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverxadatasource-class"></a>Classe SQLServerXADataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta una factory per [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) gli oggetti che viene utilizzata internamente.  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
 **Implementa:** XADataSource  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerXADataSource  
```  
  
## <a name="remarks"></a>Osservazioni  
 Oggetto che implementa l'interfaccia di SQLServerXADataSource viene generalmente registrato con un servizio di denominazione che utilizza il Java Naming and Directory Interface (JNDI).  
  
 La classe SQLServerXADataSource fornisce connessioni di database per l'utilizzo in transazioni distribuite (XA). La classe SQLServerXADataSource supporta anche il pool di connessioni fisiche. Le interfacce di SQLServerXADataSource e SQLServerXAConnection, che sono definite nel pacchetto javax.sql, vengono implementate da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
 Un oggetto SQLServerXAConnection è una connessione in pool che può partecipare in una transazione distribuita. Più precisamente, estende l'interfaccia SQLServerPooledConnection di SQLServerXAConnection aggiungendo il metodo [getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md). Questo metodo produce un [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) oggetto che può essere utilizzato da un gestore transazioni per coordinare il lavoro effettuato in questa connessione con gli altri partecipanti nella transazione distribuita. Poiché estendono l'interfaccia di SQLServerPooledConnection, SQLServerXAConnection oggetti supportano tutti i metodi di oggetti SQLServerPooledConnection. Si tratta di connessioni fisiche riutilizzabili a un'origine dati sottostante che generano handle di connessioni logiche che possono essere passati nuovamente a un'applicazione JDBC.  
  
 Gli oggetti SQLServerXAConnection vengono generati da un oggetto SQLServerXADataSource. Gli oggetti di SQLServerConnectionPoolDataSource e SQLServerXADataSource sono simili poiché vengono entrambi implementati sotto un livello di origine dati che è visibile all'applicazione JDBC. Questa architettura consente [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] supporta le transazioni distribuite in modo trasparente all'applicazione. SQLServerXADataSource può essere configurato per integrarsi con [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Distributed Transaction Coordinator (DTC) per fornire una reale elaborazione di transazioni distribuite.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
