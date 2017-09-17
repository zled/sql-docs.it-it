---
title: Metodo setClob (lang, Java.IO. Reader) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7457b8a-df31-4999-883e-8cc386a48ceb
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ee2f6f5d5e6217c93f4ac0398361f88a68a5441e
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setclob-method-javalangstring-javaioreader"></a>Metodo setClob (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il parametro designato per l'oggetto Reader specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setClob(java.lang.String parameterName,  
            java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parametri  
 *parameterName*  
  
 Oggetto **stringa** che contiene il nome del parametro.  
  
 *lettore*  
  
 Un oggetto del lettore.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setClob viene specificato dal metodo setClob nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setClob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/setclob-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
