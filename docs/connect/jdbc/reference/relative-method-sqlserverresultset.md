---
title: Metodo relative (SQLServerResultSet) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 36db05ec89818195c4b710591f1d0db71e091fe0
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
  
  

