---
title: Classe SQLServerCallableStatement | Documenti Microsoft
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
ms.assetid: 30710a63-c05d-47d9-9cf9-c087a1c76373
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 37b9942e976f1c6db89cc776f34f7639ff1c8e5e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlservercallablestatement-class"></a>Classe SQLServerCallableStatement
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Consente di specificare il nome della stored procedure da chiamare insieme ai parametri di input e di output. Questa classe fornisce anche la possibilità di recuperare il valore di stato restituito con la sintassi ? = call( ?, ..).  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Implementa:** [ISQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
 **Estende:** [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final class SQLServerCallableStatement  
```  
  
## <a name="remarks"></a>Osservazioni  
 SQLServerCallableStatement consente di specificare il nome della stored procedure da chiamare insieme ai parametri di input e outpui. SQLServerCallableStatement fornisce inoltre la possibilità di recuperare il valore di stato restituito con il `? = call( ?, ..)` sintassi.  
  
 Questa classe supporta l'annullamento del wrapping nella classe SQLServerCallableStatement, interfaccia ISQLServerCallableStatement, interfaccia Java.SQL. CallableStatement e le classi e le interfacce supportate da SQLServerPreparedStatement per l'annullamento del wrapping. Per ulteriori informazioni, vedere [wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
 Quando uno di SQLServerCallableStatement imposta metodi viene chiamato per un tipo, se tale tipo è in conflitto con il tipo specificato con [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md), viene utilizzato il tipo specificato da quest'ultimo metodo set SQLServerCallableStatement. Questo comportamento, tuttavia, può provocare errori di conversione di tipi di dati incompatibili. Se un SQLServerCallableStatement impostare il metodo non viene chiamato, il tipo specificato con il primo [registerOutParameter](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) chiamata viene utilizzata.  
  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 per è conforme all'indicazione JDBC 4.0, che un set di risultati e i conteggi aggiornamenti devono essere recuperati prima del recupero dei parametri OUT. Se i parametri OUT vengono recuperati prima dell'elaborazione completa del set di risultati e dei conteggi aggiornamenti, qualsiasi set di risultati o conteggio aggiornamenti non elaborato andrà perduto.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Riferimento all'API del Driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
