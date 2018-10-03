---
title: Metodo supportsNamedParameters (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsNamedParameters
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 158be08f-387d-4c5b-b567-a1fe590d6f16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38c3525da3af94c64a723766b96423b64cd19346
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814329"
---
# <a name="supportsnamedparameters-method-sqlserverdatabasemetadata"></a>Metodo supportsNamedParameters (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database supporta parametri denominati nelle istruzioni richiamabili.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsNamedParameters()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo supportsNamedParameters viene specificato dal metodo supportsNamedParameters nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
