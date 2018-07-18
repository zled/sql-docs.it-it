---
title: Metodo (java.util.Properties) setClientInfo | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0785a1ee2c2aa96f6058e0dba2296af524cd345e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32841236"
---
# <a name="setclientinfo-method-javautilproperties"></a>Metodo setClientInfo (java.util.Properties)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il valore delle proprietà delle informazioni client della connessione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Proprietà*  
  
 Un oggetto di proprietà che contiene l'elenco di proprietà delle informazioni client da impostare.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setClientInfo viene specificato dal metodo setClientInfo nell'interfaccia Java.SQL. Connection.  
  
 Il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] non supporta alcuna proprietà delle informazioni client. Questo metodo genera avvisi se il *proprietà* parametro di input non fa riferimento a un set di proprietà vuoto. In altre parole, questo metodo genera avvisi per le proprietà da impostare nell'applicazione. Le applicazioni devono utilizzare [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) classe per recuperare ogni avviso.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo setClientInfo &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
