---
title: Metodo setMaxRows (SQLServerStatement) | Documenti Microsoft
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
- SQLServerStatement.setMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cccc0667-589b-4655-8ea8-14ae8b2eb9dc
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a9b0a3c75d6da7805a462df3cd7ff8be8c9c9448
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="setmaxrows-method-sqlserverstatement"></a>Metodo setMaxRows (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Imposta il limite per il numero massimo di righe da qualsiasi [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) oggetto può contenere il numero specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public final void setMaxRows(int max)  
```  
  
#### <a name="parameters"></a>Parametri  
 *max*  
  
 Un **int** che indica il numero massimo di righe oppure 0 se non esiste alcun limite.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo setMaxRows viene specificato dal metodo setMaxRows nell'interfaccia Java.SQL. Statement.  
  
 Questo metodo setMaxRows ha effetto per i cursori scorrevoli dinamici. È consigliabile che l'applicazione utilizzi la sintassi SELECT TOP N SQL per limitare il numero di righe restituito da set di risultati di dimensioni potenzialmente grandi.  
  
 Quando viene chiamato il metodo setMaxRows, il [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] esegue l'istruzione SET ROWCOUNT SQL durante l'esecuzione di query dell'applicazione. In questo modo il driver JDBC limitare il numero massimo di righe interessate da tutti i [!INCLUDE[tsql](../../../includes/tsql_md.md)] istruzioni eseguite dalla query, non solo il numero di righe restituite dalla query. Se l'applicazione deve impostare un limite solo per il primo livello [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) dell'oggetto, deve utilizzare la sintassi SELECT TOP N SQL nella query anziché il metodo setMaxRows.  
  
 Per ulteriori informazioni sull'istruzione SET ROWCOUNT SQL, vedere la "[SET ROWCOUNT (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkId=139522)" argomento nella [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Classe SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
