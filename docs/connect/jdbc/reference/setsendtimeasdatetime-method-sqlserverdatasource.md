---
title: Metodo setSendTimeAsDatetime (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad4f7e8cee834619985be1ab140bc39698215060
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798239"
---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>Metodo setSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Questo metodo è stato aggiunto in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0.  
  
 Modifica l'impostazione delle **sendTimeAsDatetime** proprietà di connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sendTimeAsDateTime*  
  
 Valore booleano. Se true, comporta l'invio dei valori java.sql.Time al server come tipi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime**. Se false, comporta l'invio dei valori java.sql.Time al server come tipi [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **time**.  
  
## <a name="remarks"></a>Remarks  
 [SQLServerDataSource.getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md) restituisce l'impostazione delle **sendTimeAsDatetime** proprietà di connessione.  
  
 Per altre informazioni sul **sendTimeAsDatetime** proprietà di connessione, vedere [impostando le proprietà di connessione](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Per altre informazioni, vedere [Java configurazione come valori vengono inviati al Server](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
