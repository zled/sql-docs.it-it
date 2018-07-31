---
title: Uso dei punti di salvataggio | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3b48eb13-32ef-4fb3-8e95-dbc9468c9a44
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72b354c805a3d46dd31f6f9df308e33493c2db2c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37992933"
---
# <a name="using-savepoints"></a>Utilizzo dei punti di salvataggio
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  I punti di salvataggio consentono di eseguire il rollback di parti di transazioni. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è possibile creare un punto di salvataggio usando l'istruzione SAVE TRANSACTION savepoint_name. In seguito viene eseguita un'istruzione ROLLBACK TRANSACTION savepoint_name per eseguire il rollback del punto di salvataggio anziché della parte iniziale della transazione.  
  
 I punti di salvataggio risultano utili nelle situazioni in cui è improbabile che si verifichino degli errori. L'utilizzo di un punto di salvataggio per il rollback di parte di una transazione nel caso di errore non frequente può risultare più efficace rispetto a provare ciascuna transazione per verificare se un aggiornamento è valido prima di eseguire effettivamente l'aggiornamento. Poiché gli aggiornamenti e i rollback sono operazioni dispendiose, i punti di salvataggio sono efficaci solo se la probabilità che si verifichi l'errore è bassa e il costo del controllo preventivo della validità di un aggiornamento è relativamente alto.  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta l'utilizzo di punti di salvataggio tramite il metodo [setSavepoint](../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md) della classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Il metodo setSavepoint consente di creare un punto di salvataggio con nome o senza nome nell'ambito della transazione corrente e restituirà un oggetto [SQLServerSavepoint](../../connect/jdbc/reference/sqlserversavepoint-class.md). È possibile creare più punti di salvataggio all'interno di una transazione. Per eseguire il rollback di una transazione fino a un determinato punto di salvataggio, è possibile passare l'oggetto SQLServerSavepoint al metodo [rollback (java.sql.Savepoint)](../../connect/jdbc/reference/rollback-method-java-sql-savepoint.md).  
  
 Nell'esempio seguente viene usato un punto di salvataggio durante l'esecuzione di una transazione locale composta da due istruzioni separate nel blocco `try`. Le istruzioni vengono eseguite nella tabella Production.ScrapReason del database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] e il punto di salvataggio viene usato per eseguire il rollback della seconda istruzione. In questo modo viene eseguito il commit solo della prima istruzione nel database.  
  
 [!code[JDBC#UsingSavepoints1](../../connect/jdbc/codesnippet/Java/using-savepoints_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni con il driver JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
