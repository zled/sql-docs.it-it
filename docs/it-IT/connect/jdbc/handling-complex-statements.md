---
title: Gestione delle istruzioni complesse | Documenti Microsoft
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
ms.assetid: 6b807a45-a8b5-4b1c-8b7b-d8175c710ce0
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dc009ed538571d5b66a1240adc8b4c41cbab0a6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="handling-complex-statements"></a>Gestione delle istruzioni complesse
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si utilizza il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], potrebbe essere necessario gestire istruzioni complesse, incluse le istruzioni generate dinamicamente in fase di esecuzione. Le istruzioni complesse eseguono spesso varie attività, inclusi aggiornamenti, inserimenti ed eliminazioni. Questi tipi di istruzioni potrebbero inoltre restituire più set di risultati e parametri di output. In questi casi, nel codice Java che consente di eseguire le istruzioni non sarà possibile stabilire in anticipo i tipi e il numero degli oggetti e dei dati restituiti.  
  
 Per elaborare le istruzioni complesse in modo efficace, il driver JDBC offre vari metodi che consentono di eseguire query sugli oggetti e sui dati restituiti, in modo che l'applicazione utilizzata possa elaborarli correttamente. La chiave per l'elaborazione di istruzioni complesse è di [eseguire](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) metodo il [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) classe. Questo metodo restituisce un **booleano** valore. Quando il valore è true, il primo risultato restituito dalle istruzioni è un set di risultati. Quando il valore è false, il primo risultato restituito è un conteggio di aggiornamento.  
  
 Quando si conosce il tipo di oggetto o dati che è stati restituiti, è possibile utilizzare il [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) o [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) metodo per elaborare i dati. Per procedere con l'oggetto successivo o i dati restituiti dall'istruzione complessa, è possibile chiamare il [getMoreResults](../../connect/jdbc/reference/getmoreresults-method.md) metodo.  
  
 Nell'esempio seguente, una connessione aperta al [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio viene passato alla funzione, viene costruita un'istruzione complessa che combina una chiamata alla stored procedure con un'istruzione SQL, le istruzioni vengono eseguite, quindi un `do` ciclo utilizzato per elaborare tutti i risultati imposta e conteggi di aggiornamento che vengono restituiti.  
  
 [!code[JDBC#HandlingComplexStatements1](../../connect/jdbc/codesnippet/Java/handling-complex-statements_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Uso delle istruzioni con il driver JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  
