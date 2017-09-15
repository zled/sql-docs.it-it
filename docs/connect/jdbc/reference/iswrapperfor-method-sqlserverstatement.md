---
title: Metodo isWrapperFor (SQLServerStatement) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f3291f-d43a-476b-a656-d86168dacf6c
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: abe6782b9cf390431a20db38246184c131f9b1bd
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="iswrapperfor-method-sqlserverstatement"></a>Metodo isWrapperFor (SQLServerStatement)
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
 Il [isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md) (metodo) e [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) metodo definiti dall'interfaccia Java.SQL, che è stata introdotta in JDBC 4.0.  
  
 Se questo metodo restituisce true, la chiamata [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) con lo stesso argomento avrà esito positivo.  
  
 Per un esempio di codice, vedere [l'aggiornamento di grandi dimensioni campione di dati](../../../connect/jdbc/updating-large-data-sample.md).  
  
 Per ulteriori informazioni, vedere [wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Unwrap (metodo) &#40; SQLServerStatement &#41;](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
