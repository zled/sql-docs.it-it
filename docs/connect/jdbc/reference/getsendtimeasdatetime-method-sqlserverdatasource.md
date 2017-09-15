---
title: Metodo getSendTimeAsDatetime (SQLServerDataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 625d1e864cd0f913dbf8826372017ee99a80e41d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
 **true** se i valori Java.SQL. Time verranno inviati al server come un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** tipo. **false** se i valori Java.SQL. Time verranno inviati al server come un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **ora** tipo.  
  
## <a name="remarks"></a>Osservazioni  
 Vedere [impostando le proprietà di connessione](../../../connect/jdbc/setting-the-connection-properties.md) per ulteriori informazioni sul **sendTimeAsDatetime** proprietà di connessione.  
  
 [Setsendtimeasdatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) consente di impostare a livello di codice il **sendTimeAsDatetime** proprietà di connessione.  
  
 Per ulteriori informazioni, vedere [Java.SQL configurazione come i valori vengono inviati al Server](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
