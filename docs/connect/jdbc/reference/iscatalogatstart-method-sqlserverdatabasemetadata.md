---
title: Metodo isCatalogAtStart (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.isCatalogAtStart
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 665173d2-14c7-4ce1-954e-4adb53fb9b39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2263d4b9d7e94f4c239d7afd7fcb795063f3435
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47680359"
---
# <a name="iscatalogatstart-method-sqlserverdatabasemetadata"></a>Metodo isCatalogAtStart (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se un catalogo viene visualizzato all'inizio di un nome di tabella completo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isCatalogAtStart()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il nome del catalogo è il primo. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo isCatalogAtStart viene specificato dal metodo isCatalogAtStart nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
