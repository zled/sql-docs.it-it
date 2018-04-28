---
title: Utilizzo di più set di risultati | Documenti Microsoft
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
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1710bcf725939955b0064490bcfbe23928576430
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="using-multiple-result-sets"></a>Utilizzo di più set di risultati
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si lavora con inline SQL o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] stored procedure che restituiscono più set di risultati, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] fornisce il [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe per recuperare ogni set di dati restituiti. Inoltre, quando si esegue un'istruzione che restituisce più set di risultati, è possibile utilizzare il [eseguire](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) classe metodo SQLServerStatement, perché verrà restituito un **booleano** valore che indica se la valore restituito è un set di risultati o un conteggio aggiornamenti.  
  
 Se il metodo execute restituisce **true**, l'istruzione eseguita ha restituito uno o più set di risultati. È possibile accedere primo set di risultati tramite la chiamata al metodo getResultSet. Per determinare se sono disponibili più set di risultati, è possibile chiamare il [getMoreResults](../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md) metodo, che restituisce un **booleano** valore **true** se sono disponibili ulteriori set di risultati. Se sono disponibili più set di risultati, è possibile chiamare il metodo getResultSet nuovamente per accedere ad essi, continuare con il processo fino a quando non sono stati elaborati tutti i set di risultati. Se il metodo getMoreResults restituisce **false**, sono disponibili più gruppi di risultati al processo.  
  
 Se il metodo execute restituisce **false**, l'istruzione eseguita ha restituito un valore di conteggio aggiornamenti, è possibile recuperare tramite una chiamata di [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) metodo.  
  
> [!NOTE]  
>  Per ulteriori informazioni sui conteggi di aggiornamento, vedere [utilizzando una Stored Procedure con un conteggio di aggiornamento](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md).  
  
 Nell'esempio seguente, una connessione aperta per la [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione e viene costruita un'istruzione SQL che, quando eseguita, restituisce due set di risultati:  
  
 [!code[JDBC#UsingMultipleResultSets1](../../connect/jdbc/codesnippet/Java/using-multiple-result-sets_1.java)]  
  
 In questo caso il numero di set di risultati (pari a due) è noto. Tuttavia, il codice è scritto in modo tale che se fosse restituito un numero non noto di set di risultati, come, ad esempio, nelle chiamate a stored procedure, tutti i set verranno comunque elaborati. Per un esempio di chiamata di una stored procedure che restituisce più set di risultati con valori di aggiornamento, vedere [gestire istruzioni complesse](../../connect/jdbc/handling-complex-statements.md).  
  
> [!NOTE]  
>  Quando si effettua la chiamata al metodo getMoreResults della classe SQLServerStatement, il set di risultati restituito in precedenza viene implicitamente chiuso.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle istruzioni con il driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
