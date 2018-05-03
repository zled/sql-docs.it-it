---
title: Metodo nullsAreSortedAtStart (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.nullsAreSortedAtStart Method (SQLServerDatabaseMetaData)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 372515da-3b0e-46f6-8c0b-01b1b45c5a2f
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50f5f5470ca1541984652c12e146e519bacc118a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="nullsaresortedatstart-method-sqlserverdatabasemetadata"></a>Metodo nullsAreSortedAtStart (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera un valore che indica se i valori NULL vengono posizionati all'inizio, indipendentemente dal tipo di ordinamento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean nullsAreSortedAtStart()  
```  
  
## <a name="return-value"></a>Valore restituito  
 **true** se ordinato all'inizio. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo nullsAreSortedAtStart viene specificato dal metodo nullsAreSortedAtStart nell'interfaccia DatabaseMetaData.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
