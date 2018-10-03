---
title: Metodo supportsGroupBy (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsGroupBy
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6f368df5-e88a-4088-b0de-2b5ab655ebaa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5cd51f9e0c58ca4fda42d6bf50bbf5063d6adee3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827759"
---
# <a name="supportsgroupby-method-sqlserverdatabasemetadata"></a>Metodo supportsGroupBy (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database supporta alcuni tipi di clausola GROUP BY.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean supportsGroupBy()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se supportata. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo supportsGroupBy viene specificato dal metodo supportsGroupBy nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
