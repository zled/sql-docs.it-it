---
title: Metodo setFetchDirection (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 18176517-2fb3-4266-924d-0f01253083d2
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd846f103df1428b88a540ac20dd071d419d12d3
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setfetchdirection-method-sqlserverstatement"></a>Metodo setFetchDirection (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fornisce [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] un hint per la direzione in cui i set di righe devono essere elaborate.  
  
> [!NOTE]  
>  Attualmente, il driver JDBC ignora l'hint fornito da questo metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setFetchDirection(int nDir)  
```  
  
#### <a name="parameters"></a>Parametri  
 *nDir*  
  
 Un **int** che indica la direzione, che può essere uno dei seguenti valori di elaborazione delle righe:  
  
 FETCH_FORWARD  
  
 FETCH_REVERSE  
  
 FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setFetchDirection viene specificato dal metodo setFetchDirection nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
