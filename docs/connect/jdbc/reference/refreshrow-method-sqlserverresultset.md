---
title: Metodo refreshRow (SQLServerResultSet) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.refreshRow
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 048fe245-157f-4fd8-be75-ce54b83e02b3
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5f1a7c8a4a5381291d21f35adba178f05bc83f3f
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="refreshrow-method-sqlserverresultset"></a>Metodo refreshRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiorna la riga corrente con il relativo valore più recente nel database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void refreshRow()  
```  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo refreshRow viene specificato dal metodo refreshRow nell'interfaccia Java.SQL. ResultSet.  
  
 Non è possibile chiamare questo metodo quando il cursore si trova sulla riga di inserimento.  
  
 Tramite questo metodo un'applicazione può indicare in modo esplicito al driver JDBC di ripetere il recupero delle righe dal database. Un'applicazione potrebbe essere necessario chiamare questo metodo quando il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] è la memorizzazione nella cache o la prelettura per recuperare il valore più recente di una riga dal database. È possibile che il driver JDBC aggiorni effettivamente più righe contemporaneamente se la dimensione del recupero è maggiore di uno.  
  
 Il recupero viene ripetuto per tutti i valori in base al livello di isolamento transazione e alla sensibilità del cursore. Se questo metodo viene chiamato dopo la chiamata al metodo di aggiornamento, ma prima di chiamare il [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) (metodo), gli aggiornamenti apportati alla riga vengono persi. Se questo metodo viene chiamato frequentemente, è possibile che si verifichi una riduzione della prestazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
