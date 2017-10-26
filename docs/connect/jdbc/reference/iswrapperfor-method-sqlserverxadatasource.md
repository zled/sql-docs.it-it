---
title: Metodo isWrapperFor (SQLServerXADataSource) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d612461d-4c3f-46db-b968-ff4c80b2aa7c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ef878167c0c99be117f03ce6efffca4a9a76159e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="iswrapperfor-method-sqlserverxadatasource"></a>Metodo isWrapperFor (SQLServerXADataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo oggetto è un wrapper per l'interfaccia specificata.  
  
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
 Il [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverxadatasource.md) (metodo) e [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md) metodo definiti dall'interfaccia Java.SQL, introdotta nella specifica JDBC 4.0.  
  
 Se questo metodo restituisce true, la chiamata [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md) con lo stesso argomento avrà esito positivo.  
  
 Per ulteriori informazioni, vedere [wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Unwrap (metodo) &#40; SQLServerXADataSource &#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverxadatasource.md)   
 [Metodi di SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Membri di SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Classe SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  

