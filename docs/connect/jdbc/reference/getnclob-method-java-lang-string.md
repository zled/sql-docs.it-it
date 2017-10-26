---
title: Metodo (lang) getNClob | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be01ce56-8f13-437b-8de6-246cda5f7830
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd11b3bc0f6a43ffcc504b99b117e3eab5170749
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="getnclob-method-javalangstring"></a>Metodo getNClob (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore di JDBC **NCLOB** parametro come oggetto NClob nel linguaggio di programmazione Java.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.NClob getNClob(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterName*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 ANClobobject.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getNClob viene specificato dal metodo getNClob nell'interfaccia Java.SQL. CallableStatement.  
  
 Questo metodo supporta solo il recupero **NCHAR**, **NVARCHAR**, **NTEXT**, e **XML** parametri. La chiamata di questi metodi su altri parametri di tipi di dati causerà un'eccezione.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getNClob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  

