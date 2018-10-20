---
title: SQL Server Machine Learning Services Tutorials | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: b692b9660c3caec18c689f56ba382f8df194a9cc
ms.sourcegitcommit: b1990ec4491b5a8097c3675334009cb2876673ef
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/17/2018
ms.locfileid: "49384126"
---
# <a name="tutorials-for-sql-server-machine-learning-services"></a>Esercitazioni per SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fornisce un elenco completo delle esercitazioni, demo e le applicazioni di esempio che usano funzionalità di machine learning in SQL Server 2016 o SQL Server 2017. Iniziare da qui per informazioni su come eseguire R o Python da T-SQL, come usare contesti di calcolo remoti e locali e come ottimizzare il codice R e Python per un ambiente di produzione di SQL.

+ [Esercitazioni di Python](../tutorials/sql-server-python-tutorials.md)

+ [Esercitazioni di R](../tutorials/sql-server-r-tutorials.md)

Per altre informazioni sui requisiti e come eseguire la configurazione, vedere [prerequisiti](#bkmk_prerequisites).

## <a name="samples-and-solutions"></a>Esempi e le soluzioni

+ [Esempi](#bkmk_samples) 

    Questi scenari reali dal team di sviluppo di SQL Server viene illustrato come incorporare l'apprendimento automatico nelle applicazioni. Tutti gli esempi includono il codice che è possibile scaricare, modificare e usare nell'ambiente di produzione.

+ [Soluzioni](#bkmk_solutions) 

    I modelli dal team di Microsoft Data Science sono personalizzabili, per iniziare a usare rapidamente con machine learning. Ogni soluzione personalizzata in base a un problema specifico di attività o del settore. La maggior parte delle soluzioni sono progettata per l'esecuzione in SQL Server o in un ambiente cloud, ad esempio Azure Machine Learning. Altre soluzioni possono eseguire in Linux o in cluster di Spark o Hadoop usando Microsoft R Server o Machine Learning Server.

### <a name ="bkmk_samples"></a>Esempi del prodotto SQL Server

Questi esempi e demo fornite dal team di sviluppo di SQL Server e R Server evidenziano che modo è possibile usare analitica incorporata in applicazioni reali.

| Collegamento | Description | Applicabile a |
|------|-------------|------------|
| [Clienti di eseguire il clustering con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/) | Usare apprendimento non supervisionato per segmentare i clienti basate sui dati di vendita. In questo esempio Usa l'algoritmo rxKmeans scalabili di Microsoft R per compilare il modello di clustering. | SQL Server 2016 o SQL Server 2017 |
| [Clienti di eseguire il clustering con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/) | Informazioni su come usare l'algoritmo Kmeans per eseguire il clustering non supervisionato dei clienti. Questo esempio Usa il linguaggio di Python nel database.| SQL Server 2017 |
| [Compilare un modello predittivo con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction) | Informazioni su come un noleggio di sci potrebbe usare machine learning per prevedere i noleggi futuri, che consente al piano aziendale e personale per soddisfare la domanda futura. In questo esempio Usa gli algoritmi di Microsoft per compilare la regressione logistica e modelli di albero delle decisioni. | SQL Server 2016 o SQL Server 2017 |
| [Creare un modello predittivo usando Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/) | Compilare l'applicazione di analisi di noleggio di sci usando Python, per semplificare la pianificazione per la domanda futura. Questo esempio Usa la nuova libreria di Python **revoscalepy**, per creare un modello di regressione lineare. | SQL Server 2017 |
| [Come usare Tableau con SQL Server Machine Learning Services](https://blogs.msdn.microsoft.com/mlserver/2017/12/14/how-to-use-tableau-with-sql-server-machine-learning-services-with-r-and-python/) | Analisi dei social media e creare grafici di Tableau, usando SQL Server e R. | SQL Server 2016 o SQL Server 2017 |

### <a name="bkmk_solutions"></a>Modelli di soluzione

Il Team di Data Science di Microsoft ha fornito i modelli di soluzione che possono essere utilizzati per avviare rapidamente le soluzioni per scenari comuni. Viene fornito tutto il codice, oltre a istruzioni su come eseguire il training e distribuire un modello per l'assegnazione del punteggio utilizzando stored procedure SQL Server.

+ [Rilevamento di frodi](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [Stima personalizzata del trasferimento](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [Manutenzione predittiva](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Prevedi la ospedale durata della degenza](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

Per altre informazioni, vedere [Machine Learning Templates with SQL Server 2016 R Services (Modelli di apprendimento automatico con SQL Server 2016 R Services)](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/).

## <a name="more-resources-and-reading"></a>Altre risorse e la lettura

+ [Il motivo per cui si compilarlo?](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/01/10/sql-server-r-services-why-did-we-build-it/)

    Si desidera scoprire la vera storia dietro a R Services? Questo articolo dallo sviluppo e il team di PM che descrive l'origine e gli obiettivi di SQL Server R Services.

+ [Esercitazioni e i dati di esempio per Microsoft R](https://docs.microsoft.com/machine-learning-server/r/tutorial-introduction)

    Informazioni su Microsoft R e offerte in questa raccolta di esercitazioni rapide del pacchetto RevoScaleR. Informazioni su come scrivere codice R a una sola volta e Distribuisci ovunque, usando origini dati di RevoScaleR e contesti di calcolo remoti.

+ [Introduzione a MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-the-microsoftml-package)

  Informazioni su come usare i nuovi algoritmi del pacchetto MicrosoftML per creare modelli e le trasformazioni dei dati scalabile, ottimizzate per più contesti di calcolo.
