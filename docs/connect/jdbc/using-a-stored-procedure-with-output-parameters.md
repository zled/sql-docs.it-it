---
title: Utilizzo di una Stored Procedure con parametri di Output | Documenti Microsoft
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
ms.topic: article
ms.assetid: 1c006f27-7e99-43d5-974c-7b782659290c
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: adc77f65d20f409d0ad2ff115031d02888876863
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-a-stored-procedure-with-output-parameters"></a>Utilizzo di una stored procedure con parametri di output
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] stored procedure che è possibile chiamare è una che restituisce uno o più parametri OUT, che sono parametri che utilizza la stored procedure per restituire dati all'applicazione chiamante. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) (classe), che è possibile utilizzare per chiamare questo tipo di stored procedure ed elaborare i dati restituiti.  
  
 Quando si chiama questo tipo di stored procedure utilizzando il driver JDBC, è necessario utilizzare il `call` sequenza di escape SQL insieme con il [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. La sintassi per la `call` sequenza di escape con parametri OUT è il seguente:  
  
 `{call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  Per ulteriori informazioni sulle sequenze di escape SQL, vedere [utilizzando le sequenze di Escape SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 Quando si costruisce la `call` sequenza di escape, specificare i parametri OUT utilizzando il? (punto interrogativo), che funge da segnaposto per i valori di parametro che verranno restituiti dalla stored procedure. Per specificare un valore per un parametro OUT, è necessario specificare il tipo di dati di ciascun parametro utilizzando il [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) metodo della classe SQLServerCallableStatement prima di eseguire la stored procedure.  
  
 Il valore specificato per il parametro OUT nel metodo registerOutParameter deve essere uno dei tipi di dati JDBC contenuti in Java.SQL. Types, che a sua volta esegue il mapping a uno dei nativo [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati. Per ulteriori informazioni su Microsoft JDBC e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati, vedere [informazioni sui tipi di dati del Driver JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
 Quando si passa un valore per il metodo registerOutParameter per un parametro OUT, è necessario specificare non solo il tipo di dati da utilizzare per il parametro, ma anche la posizione ordinale del parametro o il nome del parametro nella stored procedure. Ad esempio, se la stored procedure contiene un unico parametro OUT, il valore ordinale sarà 1. Se la stored procedure contiene due parametri, il primo valore ordinale sarà 1 e il secondo sarà 2.  
  
> [!NOTE]  
>  Il driver JDBC non supporta l'utilizzo di CURSOR, SQLVARIANT, TABLE e TIMESTAMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di dati come parametri OUT.  
  
 Ad esempio, creare la seguente stored procedure nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio:  
  
```  
CREATE PROCEDURE GetImmediateManager  
   @employeeID INT,  
   @managerID INT OUTPUT  
AS  
BEGIN  
   SELECT @managerID = ManagerID   
   FROM HumanResources.Employee   
   WHERE EmployeeID = @employeeID  
END  
```  
  
 Questa stored procedure restituisce un unico parametro OUT (managerID), che è rappresentato da un numero intero, in base al parametro IN specificato (employeeID), anch'esso rappresentato da un numero intero. Il valore restituito nel parametro OUT è ManagerID, a sua volta basato sul valore EmployeeID contenuto nella tabella HumanResources.Employee.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione e [eseguire](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) metodo viene utilizzato per chiamare la stored procedure GetImmediateManager:  
  
```  
public static void executeStoredProcedure(Connection con) {  
   try {  
      CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}");  
      cstmt.setInt(1, 5);  
      cstmt.registerOutParameter(2, java.sql.Types.INTEGER);  
      cstmt.execute();  
      System.out.println("MANAGER ID: " + cstmt.getInt(2));  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
 In questo esempio vengono utilizzate le posizioni ordinali per identificare i parametri. In alternativa, è possibile identificare un parametro utilizzando il relativo nome anziché la posizione ordinale. Nell'esempio di codice seguente viene modificato l'esempio precedente per illustrare l'utilizzo di parametri denominati in un'applicazione Java. Si noti che i nomi dei parametri corrispondono ai nomi dei parametri nella definizione della stored procedure:  
  
```  
public static void executeStoredProcedure(Connection con) {  
   try {  
      CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}");  
      cstmt.setInt("employeeID", 5);  
      cstmt.registerOutParameter("managerID", java.sql.Types.INTEGER);  
      cstmt.execute();  
      System.out.println("MANAGER ID: " + cstmt.getInt("managerID"));  
      cstmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
```  
  
 }  
  
> [!NOTE]  
>  Questi esempi di utilizzano il metodo execute della classe SQLServerCallableStatement per eseguire la stored procedure. in quanto la stored procedure non ha restituito alcun set di risultati. In caso contrario, il [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) metodo viene utilizzato.  
  
 Le stored procedure possono restituire conteggi aggiornamenti e più set di risultati. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] conforme alla specifica JDBC 3.0, che indica che più set di risultati e i conteggi aggiornamenti devono essere recuperati prima che vengano recuperati i parametri OUT. Vale a dire, l'applicazione deve recuperare tutti gli oggetti ResultSet e verranno aggiornati i conteggi prima di recuperare i parametri OUT utilizzando i metodi CallableStatement.getter. In caso contrario, gli oggetti set di risultati e i conteggi di aggiornamento che non sono già stati recuperati andranno persi quando vengono recuperati i parametri OUT. Per ulteriori informazioni sui conteggi di aggiornamento e più set di risultati, vedere [utilizzando una Stored Procedure con un conteggio di aggiornamento](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) e [utilizzando più set di risultati](../../connect/jdbc/using-multiple-result-sets.md).  
  
## <a name="see-also"></a>Vedere anche  
 [USo di istruzioni con stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
