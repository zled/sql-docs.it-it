---
title: Metodo getByte (int) (SQLServerResultSet) | Documenti Microsoft
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
- SQLServerResultSet.getByte (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b22ba097-6cb8-4c5d-916b-6360dd01d2c5
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f0e44f300ccd5605307746b427b0fb1324ab6463
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getbyte-method-int-sqlserverresultset"></a>Metodo getByte (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore di indice della colonna designata nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come un **byte** nel linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public byte getByte(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnIndex*  
  
 Un **int** che indica l'indice di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **byte** valore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getByte viene specificato dal metodo getByte nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo è supportato solo in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] tipi di dati che possono restituire in modo sicuro un valore di byte, ad esempio tinyint e bit. Tutti gli altri tipi di dati genereranno un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getByte &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbyte-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

