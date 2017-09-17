---
title: Metodo (lang. String, lang) setClientInfo | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d050831-8305-48a8-bd22-207932111040
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b464cc1e1f63612557d6358f40b6c45cafc726e5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="setclientinfo-method-javalangstring-javalangstring"></a>Metodo setClientInfo (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il valore della proprietà delle informazioni client specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setClientInfo (java.lang.String name,  
                           java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parametri  
 *name*  
  
 Stringa che contiene il nome della proprietà delle informazioni client da impostare.  
  
 *Valore*  
  
 Stringa che contiene il valore per impostare la proprietà delle informazioni client.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setClientInfo viene specificato dal metodo setClientInfo nell'interfaccia Java.SQL. Connection.  
  
 Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non supporta alcuna proprietà delle informazioni client. In Microsoft JDBC Driver 2.0 questo metodo genera un avviso per una proprietà. Le applicazioni devono utilizzare [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) classe per recuperare un messaggio di avviso.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setClientInfo &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
