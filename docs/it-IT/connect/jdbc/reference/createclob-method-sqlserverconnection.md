---
title: Metodo createClob (SQLServerConnection) | Documenti Microsoft
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
ms.assetid: 58b0865a-1cde-4046-9761-51e471294023
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b6b5cec06f0976859da7eef19f462cf6dcd4a9d9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="createclob-method-sqlserverconnection"></a>Metodo createClob (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un oggetto Clob senza dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Clob createClob()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto Clob.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo createClob viene specificato dal metodo createClob nell'interfaccia Java.SQL. Connection.  
  
 Questo metodo sostituisce la necessità di [costruttore SQLServerClob &#40;SQLServerConnection, lang&#41;](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
