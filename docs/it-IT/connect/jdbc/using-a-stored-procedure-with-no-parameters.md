---
title: Utilizzando una Stored Procedure senza parametri | Documenti Microsoft
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
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 852c3a04df1227c4f99c3252072891e1962c787b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
 [USo di istruzioni con stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
