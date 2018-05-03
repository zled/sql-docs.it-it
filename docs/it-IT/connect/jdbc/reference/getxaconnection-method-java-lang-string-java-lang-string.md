---
title: Metodo (lang. String, lang) getXAConnection | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerXADataSource.getXAConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 276e0093-3d42-4f73-acc4-2b5b98245b40
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f8df6dc585f1e9d2a3686e0ee0fbdc1dae3ad28
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getxaconnection-method-javalangstring-javalangstring"></a>Metodo getXAConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tenta di stabilire una connessione di database fisica utilizzando il nome utente e la password specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public javax.sql.XAConnection getXAConnection(java.lang.String user,  
                                              java.lang.String password)  
```  
  
#### <a name="parameters"></a>Parametri  
 *user*  
  
 Oggetto **stringa** che contiene il nome utente.  
  
 *password*  
  
 Oggetto **stringa** che contiene la password.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto XAConnection.  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getXAConnection viene specificato dal metodo getXAConnection nell'interfaccia javax.SQL. XADataSource.  
  
> [!NOTE]  
>  Questo metodo viene in genere chiamato dalle implementazioni del pool di connessioni XA e non dal normale codice dell'applicazione JDBC.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getXAConnection &#40;SQLServerXADataSource&#41;](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [Metodi di SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [Membri di SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Classe SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  
