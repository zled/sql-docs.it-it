---
title: Metodo getLoginTimeout (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcaccc8a16561f43b4ada72d1e07bad291b6ec2c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>Metodo getLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce il numero di secondi che questo [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) oggetto attesa durante il tentativo di stabilire una connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** valore che rappresenta il numero di secondi di attesa.  
  
## <a name="remarks"></a>Osservazioni  
 Se l'applicazione non specifica in modo esplicito un valore di timeout, questo metodo restituisce un valore predefinito di 15 secondi.  
  
 Questo metodo getLoginTimeout viene specificato dal metodo getLoginTimeout nell'interfaccia javax.SQL.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
