---
title: Finalize (metodo) (SQLServerResultSet) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.finalize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49bc879d-822b-42da-bc20-2394865f1f0f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6762b75f40e3b1fdc0a309c67dea461b1dada974
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

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
  
  
