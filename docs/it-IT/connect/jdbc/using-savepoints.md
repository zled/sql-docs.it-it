---
title: Utilizzando i punti di salvataggio | Documenti Microsoft
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
ms.assetid: 3b48eb13-32ef-4fb3-8e95-dbc9468c9a44
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d7b02dfda385b0a5a8f5f7c1c8de710dade69b7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="using-savepoints"></a>Utilizzo dei punti di salvataggio
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  I punti di salvataggio consentono di eseguire il rollback di parti di transazioni. All'interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile creare un punto di salvataggio utilizzando l'istruzione SAVE TRANSACTION savepoint_name. In seguito viene eseguita un'istruzione ROLLBACK TRANSACTION savepoint_name per eseguire il rollback del punto di salvataggio anziché della parte iniziale della transazione.  
  
 I punti di salvataggio risultano utili nelle situazioni in cui è improbabile che si verifichino degli errori. L'utilizzo di un punto di salvataggio per il rollback di parte di una transazione nel caso di errore non frequente può risultare più efficace rispetto a provare ciascuna transazione per verificare se un aggiornamento è valido prima di eseguire effettivamente l'aggiornamento. Poiché gli aggiornamenti e i rollback sono operazioni dispendiose, i punti di salvataggio sono efficaci solo se la probabilità che si verifichi l'errore è bassa e il costo del controllo preventivo della validità di un aggiornamento è relativamente alto.  
  
 Il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta l'utilizzo di punti di salvataggio tramite il [setSavepoint](../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. Tramite il metodo setSavepoint, è possibile creare un punto di salvataggio denominato o senza nome all'interno della transazione corrente e il metodo restituirà un [SQLServerSavepoint](../../connect/jdbc/reference/sqlserversavepoint-class.md) oggetto. È possibile creare più punti di salvataggio all'interno di una transazione. Per ripristinare una transazione per un determinato punto di salvataggio, è possibile passare l'oggetto SQLServerSavepoint per il [rollback (Java.SQL. savePoint)](../../connect/jdbc/reference/rollback-method-java-sql-savepoint.md) metodo.  
  
 Nell'esempio seguente viene utilizzato un punto di salvataggio durante l'esecuzione di una transazione locale formata da due istruzioni separate nel `try` blocco. Le istruzioni vengono eseguite sulla tabella Production. ScrapReason nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio e un punto di salvataggio viene utilizzato per eseguire il rollback della seconda istruzione. In questo modo viene eseguito il commit solo della prima istruzione nel database.  
  
 [!code[JDBC#UsingSavepoints1](../../connect/jdbc/codesnippet/Java/using-savepoints_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni con il driver JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
