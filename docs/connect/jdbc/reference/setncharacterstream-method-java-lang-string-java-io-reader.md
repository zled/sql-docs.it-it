---
title: stringa di metodo all'oggetto lettore - setNCharacterStream | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd19fbb8-a878-4d98-a584-e4969d649844
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 51250ced4a6925bba1493346f48ddc6035b20005
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setncharacterstream-method-javalangstring-javaioreader"></a>Metodo setNCharacterStream (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato per l'oggetto Reader specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setNCharacterStream(java.lang.String parameterName,  
                       java.io.Reader value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterName*  
  
 Oggetto **stringa** che indica il nome del parametro.  
  
 *Valore*  
  
 Un oggetto del lettore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setNCharacterStream viene specificato dal metodo setNCharacterStream nell'interfaccia Java.SQL. CallableStatement.  
  
 Questo metodo deve essere utilizzato per **NCHAR**, **NVARCHAR**, **NTEXT**, e **XML** tipi di dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setNCharacterStream &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
