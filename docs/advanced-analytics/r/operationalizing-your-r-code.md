---
title: Rendere operativo il codice R in servizi di SQL Server Machine Learning | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: f5fa7806ad70c37c7d51c5ae2cc9606191560e58
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="operationalize-r-code-machine-learning-services"></a>Rendere operativo il codice R (servizi di Machine Learning)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Gli sviluppatori di database si occupano di integrare più tecnologie e raggruppare i risultati in modo che possano essere condivisi in tutta l'organizzazione. Lo sviluppatore del database funziona con gli sviluppatori di applicazioni, gli sviluppatori SQL e gli esperti di dati per progettare e distribuire soluzioni.

In questo articolo sono riepilogati i punti chiave per lo sviluppatore del database da considerare quando si operatività codice R con SQL Server.

## <a name="get-started-with-r-code-in-sql-server"></a>Iniziare con il codice R in SQL Server

Tradizionalmente, integrazione di soluzioni di machine learning mira ricodifica esteso per supportare l'integrazione e prestazioni. Tuttavia, lo spostamento di codice R e Python per un ambiente di produzione è molto più semplice in SQL Server Machine Learning Services, perché il codice può essere eseguito in SQL Server e utilizzando le stored procedure. È possibile continuare a usare strumenti comuni e non è necessario installare un ambiente di sviluppo R. 

Per ulteriori informazioni sulla sintassi di base, vedere:

+ [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)
+ [Utilizzo di codice R in SQL](../../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).

Per un esempio di come è possibile distribuire codice R nell'ambiente di produzione utilizzando stored procedure, vedere:

+ [Analitica nel Database per gli sviluppatori SQL](../../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md).

## <a name="optimize-your-r-code"></a>Ottimizzare il codice R

Naturalmente, conversione del codice R in SQL è più semplice se alcune ottimizzazioni vengono eseguite prima dell'operazione nel codice R o Python. Questi includono evitando i tipi di dati che causano problemi, evitare le conversioni di dati non necessari e riscrivere il codice R come una sola chiamata di funzione che può essere parametrizzata facilmente. Per altre informazioni, vedere:

+ [Librerie e tipi di dati R](r-libraries-and-data-types.md)

+ [Conversione di codice R per utilizzarlo in R Services](converting-r-code-for-use-in-sql-server.md)

+ [Generazione di una R stored procedure usando sqlrutils](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)

## <a name="integrate-r-and-python-with-applications"></a>Integrazione di R e Python con applicazioni

Poiché è possibile avviare i servizi di Machine Learning da una stored procedure, è possibile eseguire gli script R o Python da qualsiasi applicazione in grado di inviare un'istruzione T-SQL e gestire i risultati.

Ad esempio, si potrebbe ripetere il training di un modello in una pianificazione utilizzando l'attività Esegui T-SQL in Integration Services, oppure utilizzando un altro processo di pianificazione che è possibile eseguire una stored procedure.

Il punteggio è un'importante attività che può facilmente essere automatizzata o avviata da applicazioni esterne. È possibile impostare in anticipo, il modello con R, Python o una stored procedure e salvare il modello in formato binario in una tabella. Quindi, è possibile caricare il modello in una variabile come parte di una chiamata di stored procedure, utilizzando una delle seguenti opzioni per il punteggio di T-SQL:

+ [In tempo reale](../real-time-scoring.md) punteggi, ottimizzata per i batch piccoli
+ Assegnazione dei punteggi, in cui viene chiamato da un'applicazione a riga singola
+ [Assegnazione dei punteggi native](../sql-native-scoring.md), per la stima batch rapido da SQL Server senza chiamare R

Questa procedura dettagliata vengono forniti esempi di assegnazione dei punteggi utilizzando una stored procedure in batch sia la modalità a riga singola:

+ [-To-end procedura dettagliata di analisi scientifica dei dati di R in SQL Server](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Visualizzare questi modelli di soluzioni per gli esempi di integrazione in un'applicazione di punteggio:

+ [La previsione delle vendite al dettaglio](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/RetailForecasting/Introduction.md)
+ [Rilevazione di frodi](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)
+ [Cliente clustering](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/r-services/getting-started/customer-clustering)

## <a name="boost-performance-and-scale"></a>Aumentare le prestazioni e scalabilità

Sebbene il linguaggio R open source è noto per le limitazioni, il pacchetto RevoScaleR API possono operare su grandi set di dati e trarre vantaggio da multithread, multicore, multiprocesso nel database.

Se la soluzione R Usa aggregazioni complesse o comporta grandi set di dati, è possibile sfruttare le aggregazioni in memoria estremamente efficiente e gli indici columnstore di SQL Server e lasciare che il codice R gestisca i calcoli statistici e assegnazione dei punteggi.

Per ulteriori informazioni su come migliorare le prestazioni in SQL Server Machine Learning, vedere:

+ [Ottimizzazione delle prestazioni per SQL Server R Services](../../advanced-analytics/r/sql-server-r-services-performance-tuning.md)
+ [Suggerimenti di ottimizzazione delle prestazioni](https://gallery.cortanaintelligence.com/Tutorial/SQL-Server-Optimization-Tips-and-Tricks-for-Analytics-Services)

## <a name="adapt-r-code-for-other-platforms-or-compute-contexts"></a>Adattare il codice R per altre piattaforme o contesti di calcolo

Lo stesso codice R che viene eseguito sui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati può essere utilizzati con altre origini dati, ad esempio Hadoop e in altri contesti di calcolo.

Per ulteriori informazioni sulle piattaforme supportate da Microsoft R, vedere:

+ [Introduzione a Microsoft R](https://docs.microsoft.com/r-server/)

+ [Esplorare RevoScaleR](https://docs.microsoft.com/r-server/r/tutorial-r-to-revoscaler)

Per ulteriori informazioni su come ottimizzare le soluzioni di Microsoft R eseguire nei dati di grandi dimensioni o più piattaforme, vedere:

+ [Scrittura di algoritmi di suddivisione in blocchi](https://docs.microsoft.com/r-server/r/how-to-developer-write-chunking-algorithms)

+ [Elaborazione dati di grandi dimensioni in R](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips)

+ [Sviluppare un algoritmo parallelo](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

