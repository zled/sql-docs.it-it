---
title: Metodo getUserName (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getUserName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1ae81034-5de3-4f4a-b3f2-7d9d198a73af
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3247a49ecd4649988b95cc82358918a211b362a2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775839"
---
# <a name="getusername-method-sqlserverdatabasemetadata"></a>Metodo getUserName (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il nome utente così noto nel database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getUserName()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **String** contenente il nome utente.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getUserName viene specificato dal metodo getUserName nell'interfaccia java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
