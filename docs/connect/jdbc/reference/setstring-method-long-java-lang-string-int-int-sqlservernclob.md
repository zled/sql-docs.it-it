---
title: setString (long, lang, int, int) - metodo NClob | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d09ee2a09d313a192d30dc09ff07f4f3bd35d499
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>Metodo setString (long, java.lang.String, int, int) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Scrive la stringa specificata per il NCLOB a partire dalla posizione specificata, in base all'offset specificato e una lunghezza.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 La posizione in corrispondenza del quale iniziare la scrittura di **NCLOB**; la prima posizione è 1.  
  
 *str*  
  
 La stringa da scrivere il **NCLOB**.  
  
 *offset*  
  
 Offset nel *str* per avviare la lettura dei caratteri da scrivere.  
  
 *Len*  
  
 Numero di caratteri da scrivere.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setString viene specificato dal metodo setString nell'interfaccia Java.SQL. NClob.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membri di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  

