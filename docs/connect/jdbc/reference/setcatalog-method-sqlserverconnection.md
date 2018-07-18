---
title: Metodo setCatalog (SQLServerConnection) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerConnection.setCatalog
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 553c0603-c07d-436a-86eb-3ba6b51bd696
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91597c7a995fb0ecf810d3b0f58760c12784564e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32842206"
---
# <a name="setcatalog-method-sqlserverconnection"></a>Metodo setCatalog (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il nome di catalogo specificato per selezionare uno spazio secondario di questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) database dell'oggetto da utilizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void setCatalog(java.lang.String catalog)  
```  
  
#### <a name="parameters"></a>Parametri  
 *catalog*  
  
 Oggetto **stringa** che contiene il nome del catalogo.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setCatalog viene specificato dal metodo setCatalog nell'interfaccia Java.SQL. Connection.  
  
 Il *catalogo* argomento di escape per il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] automaticamente. Questo metodo imposta la proprietà di catalogo per l'oggetto connessione. Tale proprietà non viene impostata in modo implicito in altro modo.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
