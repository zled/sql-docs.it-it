---
title: Metodo getXAConnection () | Documenti Microsoft
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
- SQLServerXADataSource.getXAConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2710613-78b1-438f-b996-c7ae6f34381a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1428be2a569818d85447718042d7cf33cab66600
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getxaconnection-method-"></a>Metodo getXAConnection ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tenta di stabilire una connessione di database fisica che possa essere utilizzata in una transazione distribuita.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public javax.sql.XAConnection getXAConnection()  
```  
  
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
  
  
