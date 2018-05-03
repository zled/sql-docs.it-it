---
title: Metodo relative (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8e1c976ab8f89e18d6a86fb7d06a144a72dbe66
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="relative-method-sqlserverresultset"></a>Metodo relative (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Sposta il cursore del numero di righe specificato rispetto alla riga corrente, in direzione positiva o negativa.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean relative(int nRows)  
```  
  
#### <a name="parameters"></a>Parametri  
 *nRows*  
  
 Un **int** che indica il numero di righe da spostare.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il cursore si trova su una riga. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo relativo viene specificato dal relativo metodo nell'interfaccia Java.SQL. ResultSet.  
  
 Se si tenta di spostare oltre la prima o ultima riga nel set di risultati, il cursore viene posizionato prima o dopo la prima o ultima riga. La chiamata `relative(0)` è valido, ma non modifica la posizione del cursore.  
  
 La chiamata al metodo `relative(1)` è identica alla chiamata di [Avanti](../../../connect/jdbc/reference/next-method-sqlserverresultset.md) metodo. La chiamata al metodo `relative(-1)` è identica alla chiamata di [precedente](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md) metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
