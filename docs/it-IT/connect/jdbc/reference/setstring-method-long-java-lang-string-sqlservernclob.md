---
title: setString (long, lang) - metodo NClob | Documenti Microsoft
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
ms.assetid: 698073b2-3f0c-449c-ad68-48144698fe8f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d51e0ce96d75c2d77d9138a79b644ddf1bceb895
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setstring-method-long-javalangstring-sqlservernclob"></a>Metodo setString (long, java.lang.String) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Scrive l'oggetto specificato **stringa** per il **NCLOB** a partire dalla posizione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int setString(long pos,  
              java.lang.String str)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 La posizione in corrispondenza del quale iniziare la scrittura di **NCLOB**; la prima posizione è 1.  
  
 *str*  
  
 La stringa da scrivere il **NCLOB**.  
  
## <a name="return-value"></a>Valore restituito  
 Numero di caratteri scritti.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setString viene specificato dal metodo setString nell'interfaccia Java.SQL. NClob.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Membri di SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Classe SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
