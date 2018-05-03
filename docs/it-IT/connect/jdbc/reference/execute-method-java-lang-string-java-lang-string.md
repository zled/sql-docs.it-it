---
title: Metodo Execute (lang, lang) | Documenti Microsoft
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
- SQLServerStatement.execute (java.lang.String.java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9451c7c2-4c0d-4d1e-9b42-a26ff28e3f6a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d2ac018d3bba6a29a76559f087e22d202fcb27c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="execute-method-javalangstring-javalangstring"></a>Metodo Execute (lang, lang)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esegue l'istruzione SQL specificata, che può restituire più risultati e segnala [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] che le chiavi generate automaticamente indicate nella matrice specificata devono essere rese disponibili per il recupero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final boolean execute(java.lang.String sql,  
                             java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>Parametri  
 *sql*  
  
 Oggetto **stringa** che contiene un'istruzione SQL.  
  
 *columnNames*  
  
 Matrice di valori string che indica i nomi di colonna delle chiavi generate automaticamente che devono essere resi disponibili.  
  
## <a name="return-value"></a>Valore restituito  
 **true** se il primo risultato è un set di risultati. In caso contrario, **false**.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo execute viene specificato dal metodo execute nell'interfaccia Java.SQL. Statement.  
  
## <a name="see-also"></a>Vedere anche  
 [eseguire il metodo &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
