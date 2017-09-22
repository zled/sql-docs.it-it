---
title: Utilizzo di un'istruzione SQL con parametri | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3202b88f-ce13-44dd-982c-c6a3b0260378
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8475ea4917ffcc0d9226933b29e81b99f89345c2
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="using-an-sql-statement-with-parameters"></a>Utilizzo di istruzioni SQL con parametri
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per utilizzare i dati in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database utilizzando un'istruzione SQL contenente parametri IN, è possibile utilizzare il [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) metodo il [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) classe per restituire un [ SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) che conterrà i dati richiesti. A tale scopo, è innanzitutto necessario creare un oggetto SQLServerPreparedStatement utilizzando il [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe.  
  
 Quando si costruisce l'istruzione SQL, i parametri IN sono specificati utilizzando il carattere ? (punto interrogativo), il quale funge da segnaposto per i valori dei parametri che verranno successivamente passati all'istruzione SQL. Per specificare un valore per un parametro, è possibile utilizzare uno dei metodi setter della classe SQLServerPreparedStatement. Il metodo Set da utilizzare dipende dal tipo di dati del valore che si desidera passare all'istruzione SQL.  
  
 Quando si passa un valore al metodo Set, è necessario specificare non solo il valore effettivo da utilizzare nell'istruzione SQL, ma anche la posizione ordinale del parametro nell'istruzione stessa. Ad esempio, se l'istruzione SQL contiene un singolo parametro, il valore ordinale sarà 1. Se l'istruzione contiene due parametri, il primo valore ordinale sarà 1, mentre il secondo valore ordinale sarà 2.  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, un'istruzione SQL preparata viene costruita ed eseguita con un singolo valore di parametro di stringa e quindi i risultati vengono letti dal set di risultati.  
  
 [!code[JDBC#UsingSQLWithParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_1_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Con le istruzioni SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  