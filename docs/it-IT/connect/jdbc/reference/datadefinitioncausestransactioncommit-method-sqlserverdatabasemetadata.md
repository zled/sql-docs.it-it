---
title: Esegue il Commit delle transazioni Force istruzione di definizione dati. | Microsoft Docs
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
- SQLServerDatabaseMetaData.dataDefinitionCausesTransactionCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf04fa73-b9f1-4403-b6a0-e53d0d27c671
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c22e224e7d95104593987f21dd2801d93ea78e6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="datadefinitioncausestransactioncommit-method-sqlserverdatabasemetadata"></a>Metodo dataDefinitionCausesTransactionCommit (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se un'istruzione di definizione dei dati all'interno di una transazione forza il commit della transazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean dataDefinitionCausesTransactionCommit()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se l'istruzione DDL forza un commit. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo dataDefinitionCausesTransactionCommit viene specificato dal metodo dataDefinitionCausesTransactionCommit nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
