---
title: Metodo (SQLServerStatement) addBatch | Documenti Microsoft
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
- SQLServerStatement.addBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 95924a8b-a43c-4133-aff6-1d712e60e234
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f89b6642b8ce53358c1480bc68f617f9ba5af7e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32828472"
---
# <a name="addbatch-method-sqlserverstatement"></a>addBatch (metodo) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aggiunge il comando SQL specificato all'elenco corrente dei comandi per questo [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public void addBatch(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Oggetto **stringa** che contiene un'istruzione SQL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo addBatch viene specificato dal metodo addBatch nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
