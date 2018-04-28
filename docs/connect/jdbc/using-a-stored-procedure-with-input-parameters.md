---
title: Utilizzo di una Stored Procedure con parametri di Input | Documenti Microsoft
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
ms.assetid: 8f491b70-7d1b-42bd-964f-9a8b86af5eaa
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 64bf5a293cbe0f9fd9287a03084d66044a54337a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-a-stored-procedure-with-input-parameters"></a>Utilizzo di una stored procedure con parametri di input
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] stored procedure che è possibile chiamare è una che contiene uno o più parametri, IN cui sono parametri che possono essere usati per passare i dati alla stored procedure. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) (classe), che è possibile utilizzare per chiamare questo tipo di stored procedure ed elaborare i dati restituiti.  
  
 Quando si utilizza il driver JDBC per chiamare una stored procedure con parametri, è necessario utilizzare il `call` sequenza di escape SQL insieme con il [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. La sintassi per la `call` sequenza di escape con parametri è il seguente:  
  
 `{call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  Per ulteriori informazioni sulle sequenze di escape SQL, vedere [utilizzando le sequenze di Escape SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 Quando si costruisce la `call` sequenza di escape, specificare i parametri IN utilizzando il? (punto interrogativo), che funge da segnaposto per i valori di parametro che verranno passati alla stored procedure. Per specificare un valore per un parametro, è possibile utilizzare uno dei metodi setter della classe SQLServerPreparedStatement. Il metodo Set che è possibile utilizzare è determinato dal tipo di dati del parametro IN.  
  
 Quando si passa un valore al metodo Set, è necessario specificare non solo il valore effettivo da utilizzare nel parametro, ma anche la posizione ordinale del parametro nella stored procedure. Se, ad esempio, la stored procedure contiene un solo parametro IN, il relativo valore ordinale sarà 1. Se la stored procedure contiene due parametri, il primo valore ordinale sarà 1 e il secondo sarà 2.  
  
 Ad esempio di come chiamare una stored procedure che contiene un parametro IN, utilizzare la stored procedure uspGetEmployeeManagers nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio. Questa stored procedure accetta un singolo parametro di input denominato EmployeeID, ovvero un valore integer, e restituisce un elenco ricorsivo di dipendenti e responsabili in base al valore EmployeeID specificato. Il codice Java per la chiamata a questa stored procedure è il seguente:  
  
```  
public static void executeSprocInParams(Connection con) {  
   try {  
      PreparedStatement pstmt = con.prepareStatement("{call dbo.uspGetEmployeeManagers(?)}");  
      pstmt.setInt(1, 50);  
      ResultSet rs = pstmt.executeQuery();  
  
      while (rs.next()) {  
         System.out.println("EMPLOYEE:");  
         System.out.println(rs.getString("LastName") + ", " + rs.getString("FirstName"));  
         System.out.println("MANAGER:");  
         System.out.println(rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));  
         System.out.println();  
      }  
      rs.close();  
      pstmt.close();  
   }  
  
   catch (Exception e) {  
      e.printStackTrace();  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [USo di istruzioni con stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
