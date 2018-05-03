---
title: Metodo supportsCatalogsInDataManipulation | Documenti Microsoft
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
- SQLServerDatabaseMetaData.supportsCatalogsInDataManipulation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee1af47a-4c04-4391-83a5-54ced80218c8
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd978c2a42dc44dfd204064df3bd2a9196c58ecb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="supportscatalogsindatamanipulation-method-sqlserverdatabasemetadata"></a>Metodo supportsCatalogsInDataManipulation (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se un nome di catalogo può essere utilizzato in un'istruzione di manipolazione dei dati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsCatalogsInDataManipulation()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo supportsCatalogInDataManipulation viene specificato dal metodo nell'interfaccia DatabaseMetaData supportsCatalogInDataManipulation.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
