---
title: Metodo createStatement (int, int, int) | Documenti Microsoft
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
- SQLServerConnection.createStatement (int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2e4fa385-8f61-4394-8f75-3e839930a57d
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cabeeaf2759991bda02b3dd1f59e247c7037f15
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830636"
---
# <a name="createstatement-method-int-int-int"></a>Metodo createStatement (int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Crea un [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto che genera l'errore [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetti con il tipo specificato, concorrenza e la trattenibilità.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Statement createStatement(int nType,  
                                          int nConcur,  
                                          int nHold)  
```  
  
#### <a name="parameters"></a>Parametri  
 *resultSetType*  
  
 Il **int** valore che rappresenta il risultato set tipo.  
  
 *nConcur*  
  
 Il **int** valore che rappresenta il risultato è impostato il tipo di concorrenza.  
  
 *nHold*  
  
 Il **int** valore che rappresenta la trattenibilità.  
  
## <a name="return-value"></a>Valore restituito  
 L'oggetto istruzione.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo createStatement viene specificato dal metodo createStatement nell'interfaccia Java.SQL. Connection.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo createStatement &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)   
 [Membri di SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Classe SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
