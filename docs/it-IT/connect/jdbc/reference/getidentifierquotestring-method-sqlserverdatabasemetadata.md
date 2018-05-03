---
title: Metodo getIdentifierQuoteString (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getIdentifierQuoteString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dea35a0-56a8-412c-8cd3-6539527ff597
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e9a7cad5fae748d7dd26eb97b4fe7b655be7ccc7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getidentifierquotestring-method-sqlserverdatabasemetadata"></a>Metodo getIdentifierQuoteString (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il **stringa** che viene usato per delimitare gli identificatori SQL.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getIdentifierQuoteString()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene gli identificatori delimitati.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getIdentifierQuoteString viene specificato dal metodo getIdentifierQuoteString nell'interfaccia DatabaseMetaData.  
  
 Quando si utilizza il [!INCLUDE[msCoName](../../../includes/msconame_md.md)] Driver JDBC con un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database, questo metodo restituisce **doppie** tra virgolette ("").  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
