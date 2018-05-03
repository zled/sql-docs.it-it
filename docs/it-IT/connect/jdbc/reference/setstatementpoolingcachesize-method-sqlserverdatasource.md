---
title: Metodo (SQLServerDataSource) setStatementPoolingCacheSize | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2018
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
ms.assetid: ''
caps.latest.revision: 1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01a97116382f22e01fa649f262f35e4302e7d6d1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setstatementpoolingcachesize-method-sqlserverdatasource"></a>setStatementPoolingCacheSize metodo (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta le dimensioni della cache dell'istruzione preparata per la connessione. Funziona se disableStatementPooling è impostata su false e il valore > 0.
  
## <a name="syntax"></a>Sintassi  
  
```

public void setStatementPoolingCacheSize(boolean statementPoolingCacheSize);  
```  
  
#### <a name="parameters"></a>Parametri  
 *statementPoolingCacheSize*  
  
 Il nuovo valore della **statementPoolingCacheSize** proprietà di connessione.  

## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Osservazioni  
 Questo metodo è disponibile dal driver JDBC versione 6.4 e successivo.
 
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
