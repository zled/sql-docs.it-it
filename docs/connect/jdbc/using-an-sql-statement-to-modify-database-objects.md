---
title: Utilizzo di un'istruzione SQL per modificare gli oggetti di Database | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d5b94ff83ef6cea934efb66f6efb9394d2fa2501
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Utilizzo di un'istruzione SQL per modificare gli oggetti di database
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per modificare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti di database utilizzando un'istruzione SQL, è possibile utilizzare il [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe. Il metodo executeUpdate verrà passerà l'istruzione SQL al database per l'elaborazione e quindi restituire un valore pari a 0, perché nessuna riga è interessata.  
  
 A tale scopo, è innanzitutto necessario creare un oggetto SQLServerStatement utilizzando il [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
> [!NOTE]  
>  Le istruzioni SQL che modificano gli oggetti presenti in un database vengono definite istruzioni DDL (Data Definition Language) e includono, ad esempio, CREATE TABLE, DROP TABLE, CREATE INDEX e DROP INDEX. Per ulteriori informazioni sui tipi di istruzioni DDL supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, viene costruita un'istruzione SQL che creerà l'oggetto semplice TestTable nel database, quindi viene eseguita l'istruzione e viene visualizzato il valore restituito.  
  
 [!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Con le istruzioni SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  

