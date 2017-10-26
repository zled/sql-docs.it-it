---
title: Metodo setNClob (lang, Java.IO. Reader, long) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b95ee7-7e82-418f-8f30-948589086f63
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bb9938a611bea0db4f824d4cf95bfbbe6cfc9def
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setnclob-method-javalangstring-javaioreader-long"></a>Metodo setNClob (java.lang.String, java.io.Reader, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato per l'oggetto Reader specificato, ovvero il numero specificato di caratteri.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setNClob(java.lang.String parameterName,  
              java.io.Reader reader,  
              long length)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterName*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
 *lettore*  
  
 Un oggetto del lettore.  
  
 *length*  
  
 Oggetto **lungo** che indica il numero di caratteri nel flusso.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo deve essere utilizzato per **NCHAR**, **NVARCHAR**, **NTEXT**, e **XML** tipi di dati di parametro.  
  
 Questo metodo setNClob viene specificato dal metodo setNClob nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setNClob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  

