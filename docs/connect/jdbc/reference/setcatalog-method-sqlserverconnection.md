---
title: Metodo setCatalog (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a123f6d8a51bdb20f5a90bec39eb4b44b19f110e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622769"
---
# <a name="setcatalog-method-sqlserverconnection"></a>Metodo setCatalog (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il nome di catalogo specificato per selezionare uno spazio secondario del database di questo oggetto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) nel quale lavorare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Valore **String** contenente il nome del catalogo.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo setCatalog viene specificato dal metodo setCatalog nell'interfaccia Java.  
  
 L'argomento *catalog* viene preceduto automaticamente da caratteri di escape in [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Se si usa questo metodo, viene impostata la proprietà catalog per l'oggetto Connection. Tale proprietà non viene impostata in modo implicito in altro modo.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
