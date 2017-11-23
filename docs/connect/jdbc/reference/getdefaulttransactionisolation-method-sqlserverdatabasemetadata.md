---
title: Metodo getDefaultTransactionIsolation (SQLServerDatabaseMetaData) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.getDefaultTransactionIsolation
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 85b867ed-de5a-4879-b3f8-bce897879077
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 09cece0ac8bdf7ed1ac3dfddf38d723c36368132
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="getdefaulttransactionisolation-method-sqlserverdatabasemetadata"></a>Metodo getDefaultTransactionIsolation (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il livello di isolamento della transazione predefinito per il database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getDefaultTransactionIsolation()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il livello di isolamento transazione predefinito.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getDefaultTransactionIsolation viene specificato dal metodo getDefaultTransactionIsolation nell'interfaccia DatabaseMetaData.  
  
 Quando si utilizza il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] con un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database, questo metodo restituisce un valore di TRANSACTION_READ_COMMITTED, o **int** valore 2.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
