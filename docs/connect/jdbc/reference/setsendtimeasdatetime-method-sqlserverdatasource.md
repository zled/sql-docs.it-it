---
title: Metodo setSendTimeAsDatetime (SQLServerDataSource) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a5e9d17255ac790fbf2d1466555a2e2e877e13d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843966"
---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>Metodo setSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Driver JDBC 3.0.  
  
 Modifica l'impostazione del **sendTimeAsDatetime** proprietà di connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sendTimeAsDateTime*  
  
 Valore booleano. Se true, comporta valori Java.SQL. Time verranno inviati al server come [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** tipi. Se è false, fa sì che i valori Java.SQL. Time verranno inviati al server come [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **ora** tipi.  
  
## <a name="remarks"></a>Osservazioni  
 [Sqlserverdatasource. Getsendtimeasdatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md) restituisce l'impostazione del **sendTimeAsDatetime** proprietà di connessione.  
  
 Per ulteriori informazioni sul **sendTimeAsDatetime** proprietà di connessione, vedere [impostando le proprietà di connessione](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Per ulteriori informazioni, vedere [Java.SQL configurazione come i valori vengono inviati al Server](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
