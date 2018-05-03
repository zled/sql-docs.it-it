---
title: Metodo setLoginTimeout (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.setLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b63d1cf4-dc1b-4e35-9a56-50436642eaaf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08aa17692a03f444a304e65b6ae7ad2f872ff34a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setlogintimeout-method-sqlserverdatasource"></a>Metodo setLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il numero di secondi che questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto attesa durante il tentativo di stabilire una connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setLoginTimeout(int loginTimeout)  
```  
  
#### <a name="parameters"></a>Parametri  
 *LoginTimeout*  
  
 Un **int** valore che rappresenta il numero di secondi di attesa. Un valore pari a zero indica che il timeout è quello predefinito di sistema, impostato su 15 secondi.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setLoginTimeout viene specificato dal metodo setLoginTimeout nell'interfaccia javax.SQL.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
