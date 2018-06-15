---
title: Utilizzo della Trattenibilità | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: aa48306c-e7a0-4dcb-af21-9ebb6898e45a
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0bf10226926d3c5df21d546de042095defbbe812
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32851786"
---
# <a name="using-holdability"></a>Utilizzo della trattenibilità
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Per impostazione predefinita, i set di risultati creati in una transazione vengono mantenuti aperti non appena viene eseguito il commit della transazione nel database oppure il rollback della transazione. Può talvolta essere utile, tuttavia, chiudere il set di risultati dopo il commit della transazione. A tale scopo, il [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] supporta l'utilizzo del risultato di trattenibilità dei set.  
  
 Trattenibilità può essere impostata utilizzando il [setHoldability](../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) metodo il [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) classe. Quando si imposta la trattenibilità con il metodo setHoldability, il set di risultati costanti Hold_cursors_over_commit o ResultSet.CLOSE_CURSORS_AT_COMMIT può essere utilizzato.  
  
 Il driver JDBC supporta inoltre l'impostazione della trattenibilità quando si crea uno degli oggetti Statement. Quando si creano gli oggetti Statement che presentano overload rispetto ai parametri di trattenibilità dei set di risultati, la trattenibilità di tali oggetti deve corrispondere a quella della connessione. In caso di mancata corrispondenza, viene generata un'eccezione. In SQL Server la trattenibilità è infatti supportata solo a livello di connessione.  
  
 La trattenibilità di un set di risultati è la trattenibilità si riferisce l'oggetto SQLServerConnection che è associato a set di risultati all'ora di creazione del set di risultati per solo i cursori sul lato server. Non si applica ai cursori sul lato client. Tutti i set di risultati con cursori sul lato client verranno sempre il valore della trattenibilità è Hold_cursors_over_commit.  
  
 Per i cursori sul lato server, se connessi a SQL Server 2005 o versioni successive, l'impostazione influisce solo sulla trattenibilità dei nuovi set di risultati ancora da creare in tale connessione. Non interessa pertanto eventuali set di risultati creati in precedenza e già aperti in tale connessione. In SQL Server 2000, tuttavia, l'impostazione influisce sulla trattenibilità sia dei set di risultati esistenti che in quelli nuovi ancora da creare in tale connessione.  
  
 Nell'esempio seguente, la trattenibilità viene impostata durante l'esecuzione di una transazione locale formata da due istruzioni separate nel `try` blocco. Le istruzioni vengono eseguite sulla tabella Production. ScrapReason nel [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] database di esempio. In primo luogo, l'esempio passa alla modalità di transazione manuale impostando l'autocommit su **false**. Dopo aver disabilitata la modalità autocommit, nessuna istruzione SQL verrà eseguito il commit fino a quando l'applicazione chiama il [commit](../../connect/jdbc/reference/commit-method-sqlserverconnection.md) metodo in modo esplicito. Il codice nel blocco catch esegue il rollback della transazione se viene generata un'eccezione.  
  
 [!code[JDBC#UsingHoldability1](../../connect/jdbc/codesnippet/Java/using-holdability_1.java)]  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di transazioni con il driver JDBC](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
