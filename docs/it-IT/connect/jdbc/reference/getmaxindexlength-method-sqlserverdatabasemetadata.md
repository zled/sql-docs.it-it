---
title: Metodo getMaxIndexLength (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getMaxIndexLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7c85d021-d466-4732-85f9-53903d297041
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ecebcb87be1bbbdf5fc656ca1a978b744b36088
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getmaxindexlength-method-sqlserverdatabasemetadata"></a>Metodo getMaxIndexLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il numero massimo di byte consentito dal database in un indice, incluse tutte le parti che lo compongono.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getMaxIndexLength()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il numero massimo di byte consentiti.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getMaxIndexLength viene specificato dal metodo getMaxIndexLength nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
