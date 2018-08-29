---
title: Metodo getExtraNameCharacters (SQLServerDatabaseMetaData) | Microsoft Docs
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
- SQLServerDatabaseMetaData.getExtraNameCharacters
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a22becfe-0f07-4a15-8d11-06d4054b2369
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b29a013eac8e08f274c771d12913fb60ea410799
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784205"
---
# <a name="getextranamecharacters-method-sqlserverdatabasemetadata"></a>Metodo getExtraNameCharacters (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera tutti i caratteri aggiuntivi che possono essere utilizzati nei nomi di identificatore non racchiusi tra virgolette, ad esempio quelli non inclusi in a-z, A-Z, 0-9 e _.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getExtraNameCharacters()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Una **stringa** contenente i caratteri aggiuntivi.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getExtraNameCharacters viene specificato dal metodo getExtraNameCharacters nell'interfaccia DatabaseMetaData.  
  
 Quando si utilizza [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] con un database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il metodo restituisce i caratteri aggiuntivi $, # e \@.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membri di SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Classe SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
