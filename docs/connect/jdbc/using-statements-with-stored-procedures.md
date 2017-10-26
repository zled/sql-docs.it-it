---
title: Utilizzo di istruzioni con le Stored procedure | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0041f9e1-09b6-4487-b052-afd636c8e89a
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f617fdf969c0bdd238b07cb0def1b0a948a4d328
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-statements-with-stored-procedures"></a>Utilizzo delle istruzioni con le stored procedure
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Una stored procedure è una procedura del database, simile alle procedure di altri linguaggi di programmazione, contenuta all'interno dello stesso database. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], stored procedure possono essere create usando [!INCLUDE[tsql](../../includes/tsql_md.md)], o common language runtime (CLR) e uno di Visual Studio linguaggi di programmazione quali Visual Basic o c#. In genere, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] stored procedure possono effettuare le operazioni seguenti:  
  
-   Accettare parametri di input e restituire più valori sotto forma di parametri di output alla procedura o al batch che esegue la chiamata.  
  
-   Includere istruzioni di programmazione che eseguono le operazioni nel database, tra cui la chiamata di altre procedure.  
  
-   Restituire un valore di stato a una procedura o a un batch che esegue la chiamata per indicare l'esito positivo o negativo (e il motivo dell'esito negativo).  
  
> [!NOTE]  
>  Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] stored procedure, vedere "Informazioni sulle Stored procedure" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
 Per utilizzare i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando una stored procedure, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), e [ SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classi. La classe da utilizzare dipende dall'eventuale richiesta della stored procedure dei parametri IN (input) o OUT (output). Se la stored procedure non richiede IN o OUT, è possibile utilizzare la classe SQLServerStatement. Se la stored procedure verrà chiamata più volte o richiede solo i parametri IN, è possibile utilizzare la classe SQLServerPreparedStatement. Se la stored procedure richiede entrambi IN parametri OUT, è necessario utilizzare la classe SQLServerCallableStatement. È solo quando la stored procedure richiede i parametri OUT che è necessario l'overhead dell'utilizzo della classe SQLServerCallableStatement.  
  
> [!NOTE]  
>  Inoltre le stored procedure possono restituire conteggi di aggiornamento e più set di risultati. Per ulteriori informazioni, vedere [utilizzando una Stored Procedure con un conteggio aggiornamenti](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) e [utilizzando più set di risultati](../../connect/jdbc/using-multiple-result-sets.md).  
  
 Quando si utilizza il driver JDBC per chiamare una stored procedure con parametri, è necessario utilizzare il `call` sequenza di escape SQL insieme con il [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. La sintassi completa per la `call` sequenza di escape è come segue:  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  Per ulteriori informazioni sul `call` e altri SQL sequenze di escape, vedere [utilizzando le sequenze di Escape SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 Negli argomenti di questa sezione vengono descritti i modi in cui è possibile chiamare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] stored procedure utilizzando il driver JDBC e `call` sequenza di escape SQL.  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Utilizzando una Stored Procedure senza parametri](../../connect/jdbc/using-a-stored-procedure-with-no-parameters.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che non contengono parametri di input o di output.|  
|[Utilizzo di una Stored Procedure con parametri di Input](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che contengono parametri di input.|  
|[Utilizzo di una Stored Procedure con parametri di Output](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che contengono parametri di output.|  
|[Utilizzo di una Stored Procedure con lo stato restituito](../../connect/jdbc/using-a-stored-procedure-with-a-return-status.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che contengono valori di stato restituito.|  
|[Utilizzo di una Stored Procedure con un conteggio aggiornamenti](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)|Viene descritto come utilizzare il driver JDBC per eseguire le stored procedure che restituiscono conteggi di aggiornamento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle istruzioni con il Driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

