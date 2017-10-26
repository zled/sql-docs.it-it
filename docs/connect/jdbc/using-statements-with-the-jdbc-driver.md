---
title: Utilizzo delle istruzioni con il Driver JDBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f8f3e8f-841e-4449-9154-b5366870121f
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5e4cbbfc9d2b73d0a7c79ebc2791f588a7c8f862
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-statements-with-the-jdbc-driver"></a>Utilizzo delle istruzioni con il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] consente di utilizzare i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database in diversi modi. Il driver JDBC può essere utilizzato per eseguire istruzioni SQL nel database o per chiamare le stored procedure nel database, utilizzando sia parametri di input che di output. Il driver JDBC supporta inoltre le sequenze di escape SQL, i conteggi di aggiornamento, le chiavi generate automaticamente e l'esecuzione degli aggiornamenti in un'operazione batch.  
  
 Il driver JDBC fornisce tre classi per il recupero di dati da un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database:  
  
1.  [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) - utilizzata per l'esecuzione di istruzioni SQL senza parametri.  
  
2.  [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) , (ereditato da SQLServerStatement), utilizzata per in esecuzione le istruzioni SQL compilate che possono contenere parametri IN.  
  
3.  [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) , (ereditato da SQLServerPreparedStatement), utilizzato per l'esecuzione di stored procedure che possono contenere parametri IN, i parametri o entrambe.  
  
 Negli argomenti di questa sezione viene illustrato come utilizzare ciascuna delle tre classi di istruzioni per utilizzare i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Con le istruzioni SQL](../../connect/jdbc/using-statements-with-sql.md)|Viene descritto come utilizzare istruzioni SQL con il driver JDBC per operare con i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.|  
|[Utilizzo delle istruzioni con le Stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)|Viene descritto come utilizzare stored procedure con il driver JDBC per operare con i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.|  
|[Utilizzo di più set di risultati](../../connect/jdbc/using-multiple-result-sets.md)|Viene descritto come utilizzare il driver JDBC per recuperare i dati da più set di risultati.|  
|[Utilizzo di sequenze di Escape SQL](../../connect/jdbc/using-sql-escape-sequences.md)|Viene descritto come utilizzare le sequenze di escape SQL, quali i valori letterali di data e ora e le funzioni.|  
|[Utilizzo automatico delle chiavi generate](../../connect/jdbc/using-auto-generated-keys.md)|Viene descritto come utilizzare le chiavi generate automaticamente.|  
|[Esecuzione di operazioni Batch](../../connect/jdbc/performing-batch-operations.md)|Viene descritto come utilizzare il driver JDBC per eseguire operazioni batch.|  
|[Gestione delle istruzioni complesse](../../connect/jdbc/handling-complex-statements.md)|Viene descritto come utilizzare il driver JDBC per eseguire istruzioni complesse che consentono di eseguire varie attività e possono restituire diversi tipi di dati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del Driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

