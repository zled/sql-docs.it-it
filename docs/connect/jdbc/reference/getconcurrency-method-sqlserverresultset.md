---
title: Metodo (SQLServerResultSet) getConcurrency | Documenti Microsoft
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
- SQLServerResultSet.getConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 207e25f4-769c-4ff3-913c-3517b06208e4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94bf72d388a3bdf1ae30ee9febfc1c7c5692fc45
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32830726"
---
# <a name="getconcurrency-method-sqlserverresultset"></a>getConcurrency (metodo) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera la modalità di concorrenza dell'oggetto [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public int getConcurrency()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il tipo di concorrenza, che può essere uno dei valori seguenti:  
  
 ResultSet.CONCUR_READ_ONLY  
  
 ResultSet.CONCUR_UPDATABLE  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getConcurrency viene specificato dal metodo getConcurrency nell'interfaccia Java.SQL. ResultSet.  
  
 La concorrenza utilizzata varia a seconda di [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto che ha creato il set di risultati.  
  
 Questo metodo può essere utilizzato per determinare la concorrenza effettiva. Se selezionati dall'applicazione, saranno restituiti CONCUR_READ_ONLY o CONCUR_UPDATABLE. Se l'applicazione ha utilizzato la concorrenza predefinita, verrà restituito CONCUR_READ_ONLY.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Classe SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
