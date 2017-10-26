---
title: Esecuzione di operazioni Batch | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a576d95-7da6-4b7b-8b32-59e5b4d354c4
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 01a355319eb7c65bd87e25137e013b14406048c4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="performing-batch-operations"></a>Esecuzione di operazioni batch
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per migliorare le prestazioni quando più aggiornamenti di un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database si verificano, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] offre la possibilità di inviare più aggiornamenti come una singola unità di lavoro, denominata anche batch.  
  
 Il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), e [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) tutte classi possono essere utilizzate per inviare aggiornamenti in batch. Il [addBatch](../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md) metodo viene utilizzato per aggiungere un comando. Il [clearBatch](../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md) metodo viene utilizzato per cancellare l'elenco dei comandi. Il [executeBatch](../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md) metodo viene utilizzato per inviare tutti i comandi per l'elaborazione. Possono essere eseguite come parte di un batch solo le istruzioni DDL (Data Definition Language) e DML (Data Manipulation Language) che restituiscono un semplice conteggio di aggiornamento.  
  
 Il metodo executeBatch restituisce una matrice di **int** valori che corrispondono al conteggio aggiornamenti di ogni comando. Se uno dei comandi non riesce, viene generata una BatchUpdateException e utilizzare il metodo getUpdateCounts della classe BatchUpdateException per recuperare la matrice del conteggio di aggiornamento. Se un comando non riesce, il driver continua a elaborare i comandi rimanenti. Tuttavia, se un comando contiene un errore di sintassi sarà impossibile eseguire le istruzioni del batch.  
  
> [!NOTE]  
>  Se non è necessario utilizzare i conteggi aggiornamenti, è possibile eseguire prima un'istruzione SET NOCOUNT ON in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Il traffico di rete verrà ridotto e aumenteranno le prestazioni dell'applicazione.  
  
 Ad esempio, creare la tabella seguente nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio:  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, il metodo addBatch viene utilizzato per creare le istruzioni da eseguire e il metodo executeBatch viene chiamato per inviare il batch al database.  
  
```  
public static void executeBatchUpdate(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('X', 100)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Y', 200)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Z', 300)");  
      int[] updateCounts = stmt.executeBatch();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle istruzioni con il Driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

