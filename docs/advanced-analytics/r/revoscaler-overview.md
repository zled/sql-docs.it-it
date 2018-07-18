---
title: Pacchetto RevoScaleR in SQL Server Machine Learning | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: ecca127e3b929772c465ae7e1f694b525cc7dd00
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="revoscaler"></a>RevoScaleR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

RevoScaleR è un pacchetto delle funzioni di machine learning, fornito da Microsoft, che supporta l'analisi scientifica dei dati su larga scala.

+ Funzioni supportano l'importazione dei dati, la trasformazione dei dati, riepilogo, visualizzazione e analisi.

+ _Su larga scala_ significa che le operazioni possono essere eseguite sul set di dati molto grandi, in parallelo e su distributed file System. Gli algoritmi possono operare su set di dati che non rientrano nella memoria, utilizzando la suddivisione in blocchi e il riassemblaggio risultati una volta completate le operazioni.

+ RevoScaleR offre numerosi miglioramenti rispetto funzioni R open source. Sono disponibili funzioni RevoScaleR corrispondente a molte delle funzioni R più diffuse base. Le funzioni RevoScaleR vengono indicate con un **rx** o **Rx** prefisso per facilitarne l'identificazione.

+ RevoScaleR funge da una piattaforma per l'analisi scientifica dei dati distribuiti. Ad esempio, è possibile utilizzare le trasformazioni e contesti di calcolo RevoScaleR con gli algoritmi avanzati di [MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package). È inoltre possibile utilizzare [rxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec) per eseguire funzioni di base R in parallelo.

Per esempi di RevoScaleR in azione, vedere i blog: 

+ [Compilare e distribuire un modello predittivo con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction/)

+ [Stime di un milione con Machine Learning Server al secondo](https://blogs.msdn.microsoft.com/mlserver/2017/10/15/1-million-predictionssec-with-machine-learning-server-web-service/)

+ [Stima dei suggerimenti taxi utilizzando MicrosoftML](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2017/01/17/predicting-nyc-taxi-tips-using-microsoftml/)

+ [Ottimizzazione delle prestazioni con rxExec](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/2016/11/14/performance-optimization-when-using-rxexec-to-parallelize-algorithms/)

## <a name="how-to-get-revoscaler"></a>Come ottenere RevoScaleR

Il pacchetto RevoScaleR per R è installato disponibile nel Client di Microsoft R. Se si dispone di Machine Learning Server o si usano R in SQL Server, RevoScaleR è incluso per impostazione predefinita.

Se si usa Python, la [revoscalepy](../python/what-is-revoscalepy.md) pacchetto fornisce una funzionalità equivalente.

> [!IMPORTANT]
> Il pacchetto RevoScaleR non può essere scaricato o utilizzato in modo indipendente da dei prodotti e servizi che forniscono il.

## <a name="use-revoscaler-in-sql-server"></a>Usare RevoScaleR in SQL Server

Queste esercitazioni ed esempi viene illustrato come utilizzare le funzioni RevoScaleR per ottenere dati da SQL Server, compilazione di modelli e salvare i modelli in un database per il punteggio.

+ [Imparare a usare contesti di calcolo](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
+ [R per gli sviluppatori SQL: Train e rendere operativo un modello](../tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [Esempi di Microsoft su GitHub](https://github.com/Microsoft/SQL-Server-R-Services-Samples)

## <a name="learn-more-about-revoscaler"></a>Altre informazioni su RevoScaleR

Queste esercitazioni illustrano l'utilizzo di RevoScaleR in altri contesti di calcolo supportati da [Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), tra cui Hadoop.

+ [Che cos'è RevoScaleR?](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-revoscaler)

+ [Esplorare RevoScaleR nelle 25 funzioni](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler)

+ [Riferimento al pacchetto RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler)

