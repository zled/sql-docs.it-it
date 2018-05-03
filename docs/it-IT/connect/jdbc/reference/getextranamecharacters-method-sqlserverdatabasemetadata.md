---
title: Metodo getExtraNameCharacters (SQLServerDatabaseMetaData) | Documenti Microsoft
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
- SQLServerDatabaseMetaData.getExtraNameCharacters
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a22becfe-0f07-4a15-8d11-06d4054b2369
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43aeda1b5e4c502233195e807e631edccedb6bda
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getextranamecharacters-method-sqlserverdatabasemetadata"></a>Metodo getExtraNameCharacters (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera tutti i caratteri aggiuntivi che possono essere utilizzati nei nomi di identificatore non racchiusi tra virgolette, ad esempio quelli non inclusi in a-z, A-Z, 0-9 e _.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getExtraNameCharacters()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che contiene i caratteri aggiuntivi.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getExtraNameCharacters viene specificato dal metodo getExtraNameCharacters nell'interfaccia DatabaseMetaData.  
  
 Quando si utilizza il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] con un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] database, questo metodo restituisce il simbolo $, # e @ caratteri aggiuntivi.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
