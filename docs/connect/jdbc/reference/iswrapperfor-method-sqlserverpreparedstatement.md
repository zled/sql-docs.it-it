---
title: Metodo isWrapperFor (SQLServerPreparedStatement) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b0e591b1-73e2-4f90-967f-5555eadfc3f1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59e0427f5d0b6adbeea67d432145bc591b4352fa
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32842296"
---
# <a name="iswrapperfor-method-sqlserverpreparedstatement"></a>Metodo isWrapperFor (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo oggetto istruzione è un wrapper per l'interfaccia specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isWrapperFor(Class iface)  
```  
  
#### <a name="parameters"></a>Parametri  
 *iface*  
  
 Oggetto **classe** che definisce un'interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se l'oggetto implementa l'interfaccia o esegue il wrapping di un oggetto che implementa l'interfaccia. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Il [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md) (metodo) e [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) metodo definiti dall'interfaccia Java.SQL, introdotta nella specifica JDBC 4.0.  
  
 Se questo metodo restituisce true, la chiamata [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) con lo stesso argomento avrà esito positivo.  
  
 Per ulteriori informazioni, vedere [wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Unwrap &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
