---
title: Metodo (lang) (SQLServerResultSet) getNCharacterStream | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a117f3a3-9c25-41e1-9adb-a40e90620dd6
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f846c2c2a008fae97bfb61dbd2495ae33b05f3f2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getncharacterstream-method-javalangstring-sqlserverresultset"></a>Metodo getNCharacterStream (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore della colonna designata nella riga corrente del [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto come lettore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.io.Reader getNCharacterStream(java.lang.String columnLabel)  
```  
  
#### <a name="parameters"></a>Parametri  
 *columnLabel*  
  
 Stringa che contiene l'etichetta di colonna.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto del lettore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getNCharacterStream viene specificato dal metodo getNCharacterStream nell'interfaccia Java.SQL. ResultSet.  
  
 Questo metodo può essere utilizzato per recuperare il valore di un **nvarchar**, **nchar**, **nvarchar (max)**, **ntext**, o **xml** colonna nella riga corrente di questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto. Se si tenta di utilizzare questo metodo per recuperare valori di altri tipi di dati, verrà generata un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getNCharacterStream &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)   
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
