---
title: Metodo getClob (int) | Documenti Microsoft
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
- SQLServerCallableStatement.getClob (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 34858e03-5b93-40b1-bf21-13ad7cc7a55e
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0be52a49b5270f4ac86b3472386e15fef369ad86
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="getclob-method-int"></a>Metodo getClob (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Recupera il valore del parametro BLOB JDBC designato come oggetto Clob nel linguaggio di programmazione Java specificato all'indice del parametro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Clob getClob(int index)  
```  
  
#### <a name="parameters"></a>Parametri  
 *index*  
  
 Un **int** che indica l'indice del parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Un oggetto Clob.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getClob viene specificato dal metodo getClob nell'interfaccia Java.SQL. CallableStatement.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getClob &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getclob-method-sqlservercallablestatement.md)   
 [Membri di SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Classe SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
