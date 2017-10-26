---
title: Utilizzo di una Stored Procedure con un conteggio aggiornamenti | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fb038eeb3b3b0f14ef0ace1076244bd64949ed81
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-a-stored-procedure-with-an-update-count"></a>Utilizzo di una stored procedure con i conteggi di aggiornamento
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per modificare i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando una stored procedure, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) classe. Utilizzando la classe SQLServerCallableStatement, è possibile chiamare stored procedure che modificano i dati contenuti nel database e restituire un conteggio del numero di righe interessate, detta anche il numero di aggiornamenti.  
  
 Dopo aver impostato la chiamata alla stored procedure utilizzando la classe SQLServerCallableStatement, è quindi possibile chiamare la stored procedure utilizzando il [eseguire](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) o [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) metodo. Il metodo executeUpdate restituirà un **int** non di valore che contiene il numero di righe interessate dalla stored procedure, ma il metodo execute. Se si utilizza il metodo execute e si desidera ottenere il conteggio del numero di righe interessate, è possibile chiamare il [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) metodo dopo aver eseguito la stored procedure.  
  
> [!NOTE]  
>  Se si desidera che il driver JDBC restituisca tutti i conteggi degli aggiornamenti, inclusi i conteggi degli aggiornamenti restituiti dai trigger eventualmente attivati, impostare la proprietà della stringa di connessione lastUpdateCount su "false". Per ulteriori informazioni sulla proprietà lastUpdateCount, vedere [impostando le proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Ad esempio, creare la tabella riportata di seguito e la stored procedure e vengono inseriti i dati di esempio nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio:  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
  
CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, il metodo execute viene utilizzato per chiamare la routine UpdateTestTable archiviati e quindi il metodo getUpdateCount viene utilizzato per restituire un conteggio delle righe che sono interessate dalla stored procedure.  
  
 [!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle istruzioni con le Stored procedure](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  

