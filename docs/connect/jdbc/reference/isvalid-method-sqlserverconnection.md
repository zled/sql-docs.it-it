---
title: Metodo isValid (SQLServerConnection) | Documenti Microsoft
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
ms.topic: article
ms.assetid: 3b0a8bbf-9369-4456-9ab8-1434ccacdd7e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 169e709fa0993c651487aa5b4e67cfe76de3618e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="isvalid-method-sqlserverconnection"></a>Metodo isValid (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indica se questo [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) oggetto non è stato chiuso ed è ancora valido.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public boolean isValid(int timeout)  
```  
  
#### <a name="parameters"></a>Parametri  
 *timeout*  
  
 Un **int** che specifica il numero di secondi di attesa per la convalida della connessione.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se la connessione è valida. **false** se la connessione non è valida o non è possibile determinare la validità della connessione prima della scadenza del timeout.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo isValid viene specificato dal metodo isValid nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
