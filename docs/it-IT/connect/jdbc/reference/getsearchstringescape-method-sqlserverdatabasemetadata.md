---
title: Metodo getSearchStringEscape (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9af605053c52c273b45bbc9716e7995a30ada37e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>Metodo getSearchStringEscape (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il **stringa** che può essere utilizzato per eseguire l'escape di caratteri jolly.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene il carattere jolly di escape stringa.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getSearchStringEscape viene specificato dal metodo getSearchStringEscape nell'interfaccia DatabaseMetaData.  
  
 Questo metodo viene utilizzato solo per le ricerche con criteri di metadati. Restituisce "\\". Oggetto **stringa** criterio di ricerca è possibile eseguire l'escape di caratteri jolly ("%" e "_") e fornirli come valori letterali anteponendo una barra rovesciata. Questo si traduce "\\%" in "[%]" e "\\\_" a "[\_]".  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
