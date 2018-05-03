---
title: Metodo setNClob (int, Java.IO. Reader) | Documenti Microsoft
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
ms.assetid: 9fc9938c-b821-41c7-8df7-e21cb83a46d4
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 135d82aec8995f94ca87345cf3b4ade1466c33be
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setnclob-method-int-javaioreader"></a>Metodo setNClob (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato per l'oggetto Reader specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setNClob(int parameterIndex,  
                    java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterIndex*  
  
 Un **int** che indica l'indice del parametro.  
  
 *Lettore*  
  
 Un oggetto di lettura che indica il valore del parametro.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setNClob viene specificato dal metodo setNClob nell'interfaccia Java.SQL. PreparedStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setNClob &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
