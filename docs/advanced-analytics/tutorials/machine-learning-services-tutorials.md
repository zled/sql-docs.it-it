---
title: Esercitazioni di apprendimento macchina SQL Server | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 08/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- Python
ms.assetid: 5ccc75f6-6703-47d9-b879-9a740569b45e
caps.latest.revision: 32
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0ebeae12d6987154baa7ccb7c9417e9f92b2bbe0
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-machine-learning-tutorials"></a>Esercitazioni di SQL Server Machine Learning

In questo articolo fornisce un elenco completo delle applicazioni di esempio che utilizzano le funzionalità di machine learning in SQL Server 2016 o SQL Server 2017, esercitazioni e demo. Iniziare da qui per informazioni su come eseguire R o Python da T-SQL, utilizzare i contesti di calcolo remoti e locali e ottimizzare il codice R e Python per un ambiente di produzione di SQL.

## <a name="start-here"></a>Iniziare da qui

+ [Esercitazioni di Python](../tutorials/sql-server-python-tutorials.md)

+ [Esercitazioni di R](../tutorials/sql-server-r-tutorials.md)

Per ulteriori informazioni sui requisiti e come configurare le impostazioni, vedere [prerequisiti](#bkmk_prerequisites).

## <a name="samples-and-solutions"></a>Esempi e soluzioni

+ [Esempi](#bkmk_samples) 

    Questi scenari reali dal team di sviluppo di SQL Server viene illustrato come incorporare l'apprendimento nelle applicazioni. Tutti gli esempi includono codice che è possibile scaricare, modificare e utilizzare nell'ambiente di produzione.

+ [Soluzioni](#bkmk_solutions) 

    I modelli dal team di analisi scientifica dei dati di Microsoft sono personalizzabili, per iniziare rapidamente con l'apprendimento. Ogni soluzione personalizzata in base a un'attività specifica o di un problema di settore. Inoltre, la maggior parte delle soluzioni sono progettate per l'esecuzione in SQL Server o in un ambiente cloud, ad esempio Azure Machine Learning. Altri soluzione possa essere eseguita nei cluster di Microsoft R Server o HDI Spark.

### <a name ="bkmk_samples"></a>Esempi del prodotto SQL Server

Questi esempi e demo fornite dal team di sviluppo R Server e SQL Server evidenziano modi che è possibile utilizzare analitica incorporati nelle applicazioni reali.

+ [Clienti di eseguire il clustering con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/customerclustering/)

  Utilizzare apprendimento non supervisionato ai clienti di segmento in base ai dati di vendita. In questo esempio utilizza l'algoritmo rxKmeans scalabile da Microsoft R per compilare il modello di clustering. 
  
  Si applica a: SQL Server 2016 o SQL Server 2017

+ [NUOVO! Clienti di eseguire il clustering con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/customerclustering/)

    Informazioni su come utilizzare l'algoritmo Kmeans per eseguire il clustering non supervisionato dei clienti. In questo esempio viene utilizzato il linguaggio Python-database. 
    
    Si applica a: SQL Server 2017

+ [Compilare un modello predittivo con R e SQL Server](https://microsoft.github.io/sql-ml-tutorials/R/rentalprediction)

  Informazioni su come una società di noleggio ski potrebbe utilizzare machine learning per stimare il noleggio di futuro, che consente al piano aziendale e personale per rispondere alla domanda futura. In questo esempio Usa gli algoritmi Microsoft R per compilare una regressione logistica e un modello decision trees. 
  
  Si applica a: SQL Server 2016 o SQL Server 2017

+ [Compilare un modello predittivo con Python e SQL Server](https://microsoft.github.io/sql-ml-tutorials/python/rentalprediction/)

   Compilare l'applicazione di analisi di noleggio ski usando Python, per la pianificazione di domanda futura. Nell'esempio viene utilizzata la nuova libreria di Python, **revoscalepy**, per creare un modello di regressione lineare. 
   
   Si applica a: SQL Server 2017

### <a name="bkmk_solutions"></a>Modelli di soluzioni

Il Team di analisi scientifica dei dati di Microsoft fornisce modelli di soluzioni che possono essere utilizzati per avviare soluzioni per scenari comuni. Tutto il codice viene fornito, oltre a istruzioni su come eseguire il training e distribuire un modello per il punteggio utilizzando stored procedure SQL Server.

+ [Rilevamento di frodi](https://gallery.cortanaanalytics.com/Tutorial/Online-Fraud-Detection-Template-with-SQL-Server-R-Services-1)
+ [Stima personalizzata del trasferimento](https://gallery.cortanaanalytics.com/Tutorial/Customer-Churn-Prediction-Template-with-SQL-Server-R-Services-1)
+ [Manutenzione predittiva](https://gallery.cortanaanalytics.com/Tutorial/Predictive-Maintenance-Template-with-SQL-Server-R-Services-1)
+ [Stimare la durata ospedale di](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

Per altre informazioni, vedere [Machine Learning Templates with SQL Server 2016 R Services (Modelli di apprendimento automatico con SQL Server 2016 R Services)](https://blogs.technet.microsoft.com/machinelearning/2016/03/23/machine-learning-templates-with-sql-server-2016-r-services/).

## <a name="more-resources-and-reading"></a>Ulteriori risorse e lettura

+ [Motivo per cui è compilarlo?](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/01/10/sql-server-r-services-why-did-we-build-it/)

    Si desidera scoprire la vera storia dietro a R Services? Leggere questo articolo lo sviluppo e il team PM che descrive l'origine e gli obiettivi di SQL Server R Services.

+ [Esercitazioni e i dati di esempio per Microsoft R](https://docs.microsoft.com/r-server/r/tutorial-introduction)

    Informazioni su Microsoft R e cosa offre il pacchetto RevoScaleR in questa raccolta di esercitazioni. Informazioni su come scrivere una sola volta codice R e distribuire in qualsiasi punto, utilizzando le origini dati RevoScaleR e contesti di calcolo remoto.

+ [Introduzione a MicrosoftML](https://docs.microsoft.com/r-server/r/concept-what-is-the-microsoftml-package)

  Informazioni su come utilizzare i nuovi algoritmi nel pacchetto MicrosoftML per le trasformazioni di dati scalabili, ottimizzate per più contesti di calcolo e di modellazione avanzate.

## <a name="bkmk_Prerequisites"></a>Prerequisiti

Per eseguire queste esercitazioni, è necessario scaricare e installare il Server SQL di machine learning componenti, come descritto di seguito:

+ [Configurare SQL Server R Services](../r/set-up-sql-server-r-services-in-database.md)
+ [Impostare i servizi di SQL Server Python](../python/setup-python-machine-learning-services.md)

Con SQL Server 2017, è possibile installare R o Python o entrambi. In caso contrario il processo di installazione complessivo, architettura e requisiti sono uguali.

Dopo l'installazione di SQL Server, non dimenticare questi passaggi importanti:

1. Abilitare la funzionalità di esecuzione di script esterni eseguendo `sp_configure 'external scripts enabled', 1`. Seguire le istruzioni per riconfigurare e riavviare SQL Server.
2. Verificare che il servizio Launchpad è in esecuzione e che il thread di lavoro account utilizza possono connettersi all'istanza di SQL Server.
3. Esaminare le autorizzazioni associate all'account di accesso SQL e gli account utente di Windows che verranno eseguiti gli script R o Python. Tutti devono disporre dell'autorizzazione per eseguire gli script R o Python e connettersi all'istanza. A seconda di esempio, potrebbe essere necessario le autorizzazioni per leggere e scrivere dati e creare oggetti di database.

Per informazioni dettagliate, vedere l'articolo per alcuni problemi comuni di installazione e configurazione: [risoluzione dei problemi di Machine Learning Services](../machine-learning-troubleshooting-faq.md)

> [!NOTE]
> È possibile eseguire queste esercitazioni utilizzando un altro strumento open source R o Python. Ambiente di sviluppo e il computer SQL Server con machine learning dovranno entrambi disporre le librerie R o Python fornite da Microsoft, che supportano l'integrazione con SQL Server e l'uso di contesti di calcolo remoto.

