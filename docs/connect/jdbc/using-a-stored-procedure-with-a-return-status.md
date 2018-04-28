---
title: Utilizzo di una Stored Procedure con lo stato restituito | Documenti Microsoft
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
ms.assetid: 4b126e95-8458-41d6-af37-fc6662859f19
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c87821768fe558da9496f84d51fbe80ffec20567
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-a-stored-procedure-with-a-return-status"></a>Utilizzo di una stored procedure con stato restituito
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Oggetto [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] stored procedure che è possibile chiamare è una che restituisce uno stato o un parametro del risultato. che in genere viene utilizzato per indicare l'esito positivo o negativo della stored procedure. Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) (classe), che è possibile utilizzare per chiamare questo tipo di stored procedure ed elaborare i dati restituiti.  
  
 Quando si chiama questo tipo di stored procedure utilizzando il driver JDBC, è necessario utilizzare il `call` sequenza di escape SQL insieme con il [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe . La sintassi per la `call` sequenza di escape con un parametro return status è il seguente:  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  Per ulteriori informazioni sulle sequenze di escape SQL, vedere [utilizzando le sequenze di Escape SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 Quando si costruisce la `call` sequenza di escape, specificare il parametro return status utilizzando il? (punto interrogativo), che funge da segnaposto per il valore di parametro che verrà restituito dalla stored procedure. Per specificare un valore per un parametro return status, è necessario specificare il tipo di dati del parametro utilizzando il [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) metodo della classe SQLServerCallableStatement, prima di eseguire la stored procedure.  
  
> [!NOTE]  
>  Quando si utilizza il driver JDBC con un database di SQL Server, il valore specificato per il parametro return status nel metodo registerOutParameter sarà sempre un numero intero, è possibile specificare utilizzando il tipo di dati Java.SQL.  
  
 Inoltre, quando si passa un valore per il metodo registerOutParameter per un parametro return status, è necessario specificare non solo il tipo di dati da utilizzare per il parametro, ma anche la posizione del parametro ordinale nella chiamata alla stored procedure. Nel caso del parametro return status, la posizione ordinale sarà sempre 1 perché si tratta sempre del primo parametro nella chiamata alla stored procedure. Sebbene la classe SQLServerCallableStatement fornisce il supporto per l'utilizzo il nome del parametro per indicare il parametro specifico, è possibile utilizzare solo il numero di posizione ordinale del parametro per i parametri return status.  
  
 Ad esempio, creare la seguente stored procedure nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio:  
  
```  
CREATE PROCEDURE CheckContactCity  
   (@cityName CHAR(50))  
AS  
BEGIN  
   IF ((SELECT COUNT(*)  
   FROM Person.Address  
   WHERE City = @cityName) > 1)  
   RETURN 1  
ELSE  
   RETURN 0  
END  
```  
  
 Questa stored procedure restituisce un valore di stato uguale a 1 o 0, in base alla presenza o meno nella tabella Person.Address della città specificata nel parametro cityName.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione e [eseguire](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) metodo viene utilizzato per chiamare la stored procedure CheckContactCity:  
  
 [!code[JDBC#UsingSprocWithReturnStatus1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_1_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [USo di istruzioni con stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  
