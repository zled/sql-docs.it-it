---
title: Metodo getUpdateCount (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c4dadcaa4bfb0c2bf4698cf7b4e0be02a7d4ccf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633739"
---
# <a name="getupdatecount-method-sqlserverstatement"></a>Metodo getUpdateCount (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il risultato corrente come conteggio aggiornamenti.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final int getUpdateCount()  
```  
  
## <a name="return-value"></a>Valore restituito  
 Valore **int** contenente il conteggio aggiornamenti. Se il risultato restituito è un oggetto del set di risultati o se non è più disponibile alcun risultato, viene restituito -1.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Questo metodo getUpdateCount viene specificato dal metodo getUpdateCount nell'interfaccia Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
