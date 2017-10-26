---
title: Driver JDBC chiusa set di risultati aperti | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1739ecb5-e5cb-4807-b5a8-97c0299929d0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f2f09f2eacf96ccebb88376ba3866d4188b377d
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# Metodo autoCommitFailureClosesAllResultSets (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se tramite il driver JDBC vengono chiusi tutti i set di risultati aperti, inclusi quelli trattenibili, quando è abilitata una modalità di commit automatico e viene generata un'eccezione.  
  
## Sintassi  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## Valore restituito  
 **true** se aperto il set, inclusi quelli trattenibili, vengono chiusi quando è abilitata una modalità di commit automatico e viene generata un'eccezione. In caso contrario, **false**.  
  
## Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## Osservazioni  
 Questo metodo autoCommitFailureClosesAllResultSets viene specificato dal metodo autoCommitFailureClosesAllResultSets nell'interfaccia DatabaseMetaData.  
  
## Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

