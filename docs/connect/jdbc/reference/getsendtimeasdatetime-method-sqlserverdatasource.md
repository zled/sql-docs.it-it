---
title: Metodo getSendTimeAsDatetime (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f18836d12be9834512783f90a2d7730fcfc98798
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845209"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>Metodo getSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 Restituisce l'impostazione delle **sendTimeAsDatetime** proprietà di connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se i valori Java verranno inviati al server come un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime** tipo. **false** se i valori Java verranno inviati al server come un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **ora** tipo.  
  
## <a name="remarks"></a>Remarks  
 Visualizzare [impostando le proprietà di connessione](../../../connect/jdbc/setting-the-connection-properties.md) per altre informazioni sul **sendTimeAsDatetime** proprietà di connessione.  
  
 L'oggetto [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) consente di impostare la proprietà di connessione **sendTimeAsDatetime** a livello di codice.  
  
 Per altre informazioni, vedere [Java configurazione come valori vengono inviati al Server](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
