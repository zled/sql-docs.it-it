---
title: Metodo getLockTimeout (SQLServerDataSource) | Documenti Microsoft
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
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f01072360ecb2a917527b589d9762e5764fef0e4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getlocktimeout-method-sqlserverdatasource"></a>Metodo getLockTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un **int** valore che indica il numero di millisecondi di attesa prima che venga segnalato un timeout di blocco del database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getLockTimeout()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** valore che contiene il numero di millisecondi di attesa del database.  
  
## <a name="remarks"></a>Osservazioni  
 Il timeout di blocco è il numero di millisecondi di attesa prima che venga segnalato un timeout di blocco per il database. Il valore predefinito -1 indica un'attesa illimitata. Se specificato, questo valore diventerà l'impostazione predefinita per tutte le istruzioni sulla connessione.  
  
> [!NOTE]  
>  Un valore pari a 0 indica che non vi sarà attesa. Se la proprietà lockTimeout non è impostata, il metodo getLockTimeout restituisce il valore predefinito -1.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
