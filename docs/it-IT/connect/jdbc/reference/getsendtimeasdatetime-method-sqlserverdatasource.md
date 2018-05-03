---
title: Metodo getSendTimeAsDatetime (SQLServerDataSource) | Documenti Microsoft
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
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f6df7971a2f594f3ce66c4e8a8d7bdf1b92962c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Metodo getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0.  
  
 Restituisce l'impostazione del **sendTimeAsDatetime** proprietà di connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se Java verranno invece inviati al server come un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** tipo. **false** se Java verranno invece inviati al server come un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **tempo** tipo.  
  
## <a name="remarks"></a>Osservazioni  
 Vedere [impostando le proprietà di connessione](../../../connect/jdbc/setting-the-connection-properties.md) per ulteriori informazioni sul **sendTimeAsDatetime** proprietà di connessione.  
  
 [Setsendtimeasdatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) consente di impostare a livello di codice il **sendTimeAsDatetime** proprietà di connessione.  
  
 Per ulteriori informazioni, vedere [Java.SQL configurazione come i valori vengono inviati al Server](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
