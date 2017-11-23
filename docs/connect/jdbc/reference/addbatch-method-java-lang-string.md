---
title: Metodo (lang) addBatch | Documenti Microsoft
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
apiname: SQLServerPreparedStatement.addBatch (java.lang.String)
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 093f6c3b-49a6-4043-9993-bd0482de04dd
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ffd607b4ef4ac3231c52a9928f94778f69b491fd
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2017
---
# <a name="addbatch-method-javalangstring"></a>Metodo addBatch (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiunge il comando SQL specificato all'elenco corrente dei comandi per questo [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *SQL*  
  
 Oggetto **stringa** che contiene un'istruzione SQL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo addBatch viene specificato dal metodo addBatch nell'interfaccia Java.SQL. Statement.  
  
 Chiamare questo metodo comporterà un'eccezione poiché l'istruzione SQL per l'oggetto SQLServerPreparedStatement non viene specificato quando viene creato l'oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo addBatch &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md)   
 [Membri di SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
