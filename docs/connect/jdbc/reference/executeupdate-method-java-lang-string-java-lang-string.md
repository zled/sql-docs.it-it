---
title: Metodo executeUpdate (lang, lang) | Documenti Microsoft
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
- SQLServerStatement.executeUpdate (java.lang.String[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2f44a689-65c8-4c94-9574-e9c08ea7918e
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 53682225a680d9913fd03e4e7a52beee729eecbc
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="executeupdate-method-javalangstring-javalangstring"></a>Metodo executeUpdate (lang, lang)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Esegue l'istruzione SQL specificata e segnala [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] che le chiavi generate automaticamente indicate nella matrice specificata devono essere rese disponibili per il recupero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final int executeUpdate(java.lang.String sql,  
                               java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>Parametri  
 *SQL*  
  
 Oggetto **stringa** che contiene un'istruzione SQL.  
  
 *columnNames*  
  
 Matrice di tipo **stringa** che indica i nomi di colonna delle chiavi generate automaticamente devono essere rese disponibili.  
  
## <a name="return-value"></a>Valore restituito  
 Un **int** che indica il numero di righe interessate, 0 se si utilizza un'istruzione DDL.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo executeUpdate viene specificato dal metodo executeUpdate nell'interfaccia Java.SQL. Statement.  
  
 Se l'esecuzione di una stored procedure restituisce un conteggio di aggiornamento che è maggiore di uno o genera più set di risultati, utilizzare il [eseguire](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) metodo per eseguire la stored procedure.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo executeUpdate &#40; SQLServerStatement &#41;](../../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md)   
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
