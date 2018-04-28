---
title: Metodo getSubString (SQLServerClob) | Documenti Microsoft
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
ms.topic: article
apiname:
- SQLServerClob.getSubString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf915590-a883-4403-befa-5b5bb42f34d8
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 57bfbc4553d33005a81ee71864551c1b91b481f6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="getsubstring-method-sqlserverclob"></a>Metodo getSubString (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce una copia della sottostringa specificata nell'oggetto CLOB in base alla posizione di inizio specificata e al numero di caratteri da copiare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.lang.String getSubString(long pos,  
                                     int length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *POS*  
  
 Primo carattere della sottostringa da estrarre. Il primo carattere si trova nella posizione 1.  
  
 *lunghezza*  
  
 Numero di caratteri consecutivi da copiare.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** che rappresenta la sottostringa specificata nell'oggetto CLOB.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getSubString viene specificato dal metodo getSubString nell'interfaccia Java.SQL. Clob.  
  
 Se si tenta di ottenere zero caratteri da un oggetto CLOB Null o di lunghezza zero, viene restituita una stringa vuota. Se si tenta di ottenere un numero qualsiasi di caratteri in qualsiasi posizione diversa da 1 in un oggetto CLOB di lunghezza zero, verrà generata un'eccezione di posizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [Membri di SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [Classe SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
