---
title: Metodo getSQLKeywords (SQLServerDatabaseMetaData) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSQLKeywords
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a2a0dfbb-11ec-429f-aea6-8f44148ebb8e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4ea59fc45d3615091b0f1efeb24d5650feab09c9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32838836"
---
# <a name="getsqlkeywords-method-sqlserverdatabasemetadata"></a>Metodo getSQLKeywords (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un elenco delimitato da virgole di tutte le parole chiave SQL del database che non sono anche parole chiave SQL92.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getSQLKeywords()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene le parole chiave SQL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getSQLKeywords viene specificato dal metodo getSQLKeywords nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
