---
title: Gestione delle dimensioni delle transazioni | Documenti Microsoft
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
ms.assetid: 82900342-bc80-445f-98a4-468a303aae1e
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c36592d2460dca27a172be763ef2cd289b6571f8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="managing-transaction-size"></a>Gestione delle dimensioni delle transazioni
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quando si utilizzano le transazioni, è importante garantire che siano il più brevi possibile. La modalità predefinita autocommit, che è possibile attivare o disattivare utilizzando il [setAutoCommit](../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md) metodo, verrà eseguito il commit di ogni azione. e costituisce il metodo di lavoro più semplice per la maggior parte degli sviluppatori.  
  
 Quando si utilizzano transazioni manuali, assicurarsi che il codice esegua il commit della transazione il più rapidamente possibile. Se una transazione viene tenuta aperta, gli altri utenti non possono accedere ai dati. Durante la programmazione è ad esempio consigliabile inserire una chiamata di rollback nel blocco catch e una chiamata di commit nel blocco finally. Questo dipende tuttavia dalla progettazione dell'applicazione.  
  
 Contenendo la dimensione delle transazioni, è possibile creare una concorrenza migliore. Se ad esempio si avvia una transazione manuale e si modificano 10.000 righe in una tabella costituita da 20.000 righe, metà tabella sarà completamente bloccata per tutti gli altri utenti, anche se stanno solo leggendo i dati. Riducendo le modifiche a 2.000 righe, si lascia disponibile il 90% della tabella.  
  
 Assicurarsi inoltre di utilizzare l'impostazione di timeout del blocco se per l'applicazione si prevedono situazioni di blocco ed è necessario impostare un timeout per tali situazioni. È possibile farlo tramite il [setLockTimeout](../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md) metodo. L'impostazione predefinita per il timeout del blocco è -1, che significa che il blocco ha un tempo indefinito. È possibile impostare il timeout del blocco su 30 secondi, che significa che se una connessione bloccata viene bloccata da un'altra connessione, si verifica il timeout entro 30 secondi.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso del driver JDBC per il miglioramento di prestazioni e affidabilità](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
