---
title: Metodo getMaxBinaryLiteralLength (SQLServerDatabaseMetaData) | Documenti Microsoft
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
apiname:
- SQLServerDatabaseMetaData.getMaxBinaryLiteralLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 42e49ff9-8072-44e4-ad75-c864c3a4ad8c
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5be88f0dc1058db0efe1c7a4363e255055daadc2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getmaxbinaryliterallength-method-sqlserverdatabasemetadata"></a>Metodo getMaxBinaryLiteralLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il numero massimo di caratteri esadecimali consentiti dal database in un valore letterale binario inline.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getMaxBinaryLiteralLength()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il numero massimo di caratteri esadecimali.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getMaxBinaryLiteralLength viene specificato dal metodo getMaxBinaryLiteralLength nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
