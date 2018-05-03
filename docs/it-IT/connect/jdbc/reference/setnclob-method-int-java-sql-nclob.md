---
title: Metodo setNClob (int, Java.SQL. NClob) | Documenti Microsoft
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
ms.assetid: 48c8aa2a-4185-4837-b592-830e60f8ca0b
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b8c17692914749be6d7e56c315ca0dd00ebd3d45
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setnclob-method-int-javasqlnclob"></a>Metodo setNClob (int, java.sql.NClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato sull'oggetto NClob specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setNClob(int parameterIndex,  
              java.sql.NClob value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterIndex*  
  
 Un **int** che indica l'indice del parametro.  
  
 *Valore*  
  
 Un oggetto NClob che indica il valore del parametro.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setNClob viene specificato dal metodo setNClob nell'interfaccia Java.SQL. PreparedStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setNClob &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
