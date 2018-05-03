---
title: Metodo supportsSchemasInTableDefinitions | Documenti Microsoft
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
- SQLServerDatabaseMetaData.supportsSchemasInTableDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3326b1b0-53e2-42ae-9ff7-98e8c7017ffa
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b87c620813b76e6c798756807368bad138f730a4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supportsschemasintabledefinitions-method-sqlserverdatabasemetadata"></a>Metodo supportsSchemasInTableDefinitions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se un nome di schema può essere utilizzato in un'istruzione di definizione delle tabelle.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsSchemasInTableDefinitions()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo supportsSchemasInTableDefinitions viene specificato dal metodo supportsSchemasInTableDefinitions nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
