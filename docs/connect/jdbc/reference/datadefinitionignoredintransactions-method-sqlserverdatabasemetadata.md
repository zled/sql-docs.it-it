---
title: Database Ignora istruzione di definizione dei dati all'interno delle transazioni | Documenti Microsoft
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
- SQLServerDatabaseMetaData.dataDefinitionIgnoredInTransactions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1674fb46-43a7-46d0-9f05-cf993d3bc032
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7551216ae4f6f3ff54611497c0e3d6d7ba5b3919
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32828796"
---
# <a name="datadefinitionignoredintransactions-method-sqlserverdatabasemetadata"></a>Metodo dataDefinitionIgnoredInTransactions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se il database ignora un'istruzione di definizione dei dati all'interno di una transazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean dataDefinitionIgnoredInTransactions()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se le istruzioni DDL vengono ignorate all'interno di transazioni. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo dataDefinitionIgnoredInTransactions viene specificato dal metodo dataDefinitionIgnoredInTransactions nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
