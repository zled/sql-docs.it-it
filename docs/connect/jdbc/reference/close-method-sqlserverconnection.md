---
title: Metodo Close (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f0f26585-bdf7-4737-b434-8c7e115c8e94
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c62d7187305bf0b5122d60d0ddf728bd1a98549
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597770"
---
# <a name="close-method-sqlserverconnection"></a>Metodo close (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rilascia immediatamente le risorse JDBC e di database dell'oggetto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) invece di attendere il rilascio automatico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo close viene specificato dal metodo close nell'interfaccia java.sql.Connection.  
  
 La chiamata del metodo close durante una transazione comporta il rollback della transazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
