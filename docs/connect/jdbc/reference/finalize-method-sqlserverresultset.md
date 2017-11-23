---
title: Finalize (metodo) (SQLServerResultSet) | Documenti Microsoft
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
apiname: SQLServerResultSet.finalize
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 49bc879d-822b-42da-bc20-2394865f1f0f
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7f3245c2e1eeae5502dad053608d988938211c59
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="finalize-method-sqlserverresultset"></a>Finalize (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Chiude in modo esplicito questo [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void finalize()  
```  
  
## <a name="remarks"></a>Osservazioni  
 Chiude il set di risultati se tale operazione non viene eseguita dall'applicazione. Questo metodo esiste solo per la conformità alla specifica JDBC. Poiché Java Virtual Machine (JVM) non garantisce l'esecuzione di un finalizzatore, le applicazioni che non consentono la chiusura in modo esplicito dei relativi set di risultati possono ancora generare un deadlock su un'altra istruzione che sta utilizzando la stessa connessione ed è bloccata su una risorsa server comune, ad esempio i blocchi a livello di riga.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
