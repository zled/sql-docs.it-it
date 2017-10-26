---
title: Utilizzando una Stored Procedure senza parametri | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4600b2cd527fdb6261ca700a19bf2e5c004bc31c
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-a-stored-procedure-with-no-parameters"></a>Utilizzo di una stored procedure senza parametri
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Il tipo più semplice di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] stored procedure che è possibile chiamare è una che non contiene parametri e restituisce un singolo set di risultati. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) (classe), che è possibile utilizzare per chiamare questo tipo di stored procedure ed elaborare i dati restituiti.  
  
 Quando si utilizza il driver JDBC per chiamare una stored procedure senza parametri, è necessario utilizzare il `call` sequenza di escape SQL. La sintassi per la `call` sequenza di escape senza parametri è come segue:  
  
 `{call procedure-name}`  
  
> [!NOTE]  
>  Per ulteriori informazioni sulle sequenze di escape SQL, vedere [utilizzando le sequenze di Escape SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 Ad esempio, creare la seguente stored procedure nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio:  
  
```  
CREATE PROCEDURE GetContactFormalNames   
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName   
   FROM Person.Contact  
END  
```  
  
 Questa stored procedure restituisce un solo set di risultati contenente una colonna di dati che corrispondono a una combinazione di titolo, nome e cognome dei primi dieci contatti presenti nella tabella Person.Contact.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione e [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) metodo viene utilizzato per chiamare la stored procedure getcontactformalnames:.  
  
```  
public static void executeSprocNoParams(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
  
      while (rs.next()) {  
         System.out.println(rs.getString("FormalName"));  
      }  
      rs.close();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle istruzioni con le Stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  

