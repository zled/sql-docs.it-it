---
title: Metodo supportsPositionedUpdate (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsPositionedUpdate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f963fb70-377d-43f5-8d56-326591f6d3e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c44dc72058a3bd8b78dd78676eb5478450b2f53f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804269"
---
# <a name="supportspositionedupdate-method-sqlserverdatabasemetadata"></a>Metodo supportsPositionedUpdate (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database supporta le istruzioni UPDATE posizionate.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsPositionedUpdate()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo supportsPositionedUpdate viene specificato dal metodo supportsPositionedUpdate nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
