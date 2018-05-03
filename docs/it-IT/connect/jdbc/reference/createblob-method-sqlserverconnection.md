---
title: Metodo createBlob (SQLServerConnection) | Documenti Microsoft
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
ms.assetid: 630a93b0-6e3c-4255-a007-1097ce0ee243
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6d149dfe7c29b129b023c70bf983f11d185582f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="createblob-method-sqlserverconnection"></a>Metodo createBlob (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un oggetto Blob senza dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Blob createBlob()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto Blob.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo createBlob viene specificato dal metodo createBlob nell'interfaccia Java.SQL. Connection.  
  
 Questo metodo sostituisce la necessità di [costruttore SQLServerBlob &#40;SQLServerConnection, byte&#41;](../../../connect/jdbc/reference/sqlserverblob-constructor-sqlserverconnection-byte.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
