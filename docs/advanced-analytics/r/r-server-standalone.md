---
title: Machine Learning Server (Standalone) di SQL Server e R Server (Standalone) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a8cdceabc26c55b6eade57712fa610d3e84808f5
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174788"
---
# <a name="sql-server-machine-learning-server-standalone-and-r-server-standalone"></a>Machine Learning Server (Standalone) di SQL Server e R Server (Standalone)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Un server autonomo è un'installazione dei componenti di apprendimento automatico, articolata come funzionalità R e Python, eseguiti indipendentemente dalle istanze del motore di database SQL Server. È possibile installare un server autonomo autonomamente, senza dipendenze in SQL Server. Poiché un server autonomo è indipendente da attività di SQL Server, configurazione e amministrazione e gli strumenti sono più simili a una versione non-SQL di Machine Learning Server, è possibile leggere nella [questo articolo](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server).

Descrive come server autonomo machine learning consiste nel fornire un ambiente di sviluppo ricco di funzionalità, con l'elaborazione distribuita e parallela dei carichi di lavoro di R e Python in piccole e grandi set di dati, utilizzando i pacchetti proprietari e motori di calcolo installato con il server. I pacchetti R e Python in un server autonomo sono identici a quelli forniti in un'installazione di SQL Server (In-Database), che consente la portabilità del codice e [cambio di contesto di calcolo](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

Gli sviluppatori di motivo principale scelgono che server autonomo machine learning consiste nello spostare oltre i vincoli di memoria e l'elaborazione di R e Python open source. Server autonomi possono caricare ed elaborare grandi quantità di dati su più core e aggregare i risultati in un singolo output consolidato. Le funzioni e gli algoritmi sono progettati per operare sia scalabilità che utilità: recapito di analitica predittiva, modellazione statistica, visualizzazioni dei dati e avanguardia algoritmi di machine learning in un prodotto commerciale server progettato e supportato da Microsoft.

In generale, è consigliabile che considera (autonomo) e (In-Database) installazioni come si escludono a vicenda per evitare conflitti di risorse, ma se si dispone di sufficienti risorse, non è nessun divieto di installarle entrambi nello stesso computer fisico.

Può avere solo un server autonomo nel computer: uno [Machine Learning Server (standalone) di SQL Server 2017](../install/sql-machine-learning-standalone-windows-install.md) oppure [SQL Server 2016 R Server (Standalone)](../install/sql-r-standalone-windows-install.md). Prima di installare una versione diversa, è necessario disinstallare manualmente una versione.

## <a name="components-of-a-standalone-server"></a>Componenti di un server autonomo

SQL Server 2016 è solo R. SQL Server 2017 supporta R e Python. La tabella seguente descrive le funzionalità di ogni versione.

| Componente | Description |
|-----------|-------------|
| Pacchetti R | [RevoScaleR](revoscaler-overview.md) è la libreria primaria per R scalabili con le funzioni per la manipolazione dei dati, trasformazione, visualzation e analisi.  <br/>[MicrosoftML (R)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) aggiunge algoritmi di machine learning per creare modelli personalizzati per l'analisi del sentiment, analisi delle immagini e analisi del testo. <br/>[mrsdeploy](operationalization-with-mrsdeploy.md) offerte web distribuzione del servizio (in SQL Server 2017 solo). <br/>[olapR](how-to-create-mdx-queries-using-olapr.md) di specificare le query MDX in R.|
| Microsoft R Open (MRO) | [MRO](https://mran.microsoft.com/open) è distribuzione open source di Microsoft di R. Sono inclusi il pacchetto e dell'interprete. Usare sempre la versione di MRO in bundle nel programma di installazione. |
| Strumenti R | Prompt dei comandi e le finestre della console R sono gli strumenti standard in una distribuzione di R. Trovare in \Programmi\Microsoft SQL Server\140\R_SERVER\bin\x64. |
| Esempi di R e gli script |  Pacchetti open source di R e RevoScaleR includono set di dati incorporato in modo che è possibile creare ed eseguire lo script usando i dati pre-installati. La ricerca di essi in \Programmi\Microsoft SQL Server\140\R_SERVER\library\datasets e \library\RevoScaleR. |
| Pacchetti Python | [revoscalepy](../python/what-is-revoscalepy.md) è la libreria primaria per Python scalabile con funzioni di manipolazione dei dati, trasformazione, visualzation e analisi. <br/>[microsoftml (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) aggiunge algoritmi di machine learning per creare modelli personalizzati per l'analisi del sentiment, analisi delle immagini e analisi del testo.  |
| Strumenti Python | Lo strumento della riga di comando di Python predefinito è utile per test ad hoc e attività. Trovare lo strumento in \Programmi\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda è una distribuzione open source di Python e i pacchetti essenziali. |
| Gli script ed esempi di Python | Come con R, Python include set di dati incorporato e gli script. Trovare i dati revoscalepy \Programmi\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample-data. |
| Modelli con training preliminare in R e Python | I modelli con training preliminare sono supportati e utilizzabile in un server autonomo, ma non è possibile installarli tramite l'installazione di SQL Server. Programma di installazione di Microsoft Machine Learning Server fornisce i modelli, è possibile installare gratuitamente. Per altre informazioni, vedere [Install pretrained modelli di machine learning in SQL Server](../install/sql-pretrained-models-install.md). |

## <a name="get-started-step-by-step"></a>Introduzione a dettagliate

Iniziare con il programma di installazione, collegare i file binari dello strumento di sviluppo preferito e scrivere il primo script.

### <a name="step-1-install-the-software"></a>Passaggio 1: Installare il software

Installare una di queste versioni:

+ [Machine Learning Server (standalone) di SQL Server 2017](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (Standalone) - solo R](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Passaggio 2: Configurare uno strumento di sviluppo

Configurare gli strumenti di sviluppo per usare i file binari di Machine Learning Server. Per altre informazioni su Python, vedere [i file binari Python collegamento](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Per istruzioni su come connettersi in R Studio, vedere [con diverse versioni di R](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) e scegliere lo strumento C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64. È inoltre possibile tentare [R Tools per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation). 

### <a name="step-3-write-your-first-script"></a>Passaggio 3: Scrivere il primo script

Scrivere script R o Python usando funzioni di RevoScaleR e revoscalepy di algoritmi di machine learning.
  
  + [Esplorare R e in 25 funzioni RevoScaleR](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): inizio con i comandi R di base e quindi lo stato di avanzamento per le funzioni analitiche distribuibili RevoScaleR che forniscono prestazioni elevate e scalabilità per le soluzioni R. Include versioni parallelizzabili di molti dei più diffusi pacchetti di modellazione R, tra cui clustering K-Means, alberi delle decisioni e foreste delle decisioni, nonché strumenti per la modifica dei dati.

  + [Guida introduttiva: Un esempio di classificazione binaria con il pacchetto Python microsoftml](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): creare un modello di classificazione binaria usando le funzioni di microsoftml e il set di dati noto esempio breast cancer.

Scegliere il linguaggio migliore per l'attività. R è ideale per i calcoli statistici difficili da implementare tramite SQL. Per le operazioni sui dati basata su set sfrutta la potenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ottenere prestazioni ottimali. Usare il motore di database in memoria per i calcoli molto veloci su colonne.

### <a name="step-4-operationalize-your-solution"></a>Passaggio 4: Rendere operativa la soluzione

Server autonomi è possono usare la [operazionalizzazione](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) funzionalità del non-SQL-marchio [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). È possibile configurare un server autonomo per l'operazionalizzazione, che offre questi vantaggi: distribuire e ospitare il codice come servizi web, Esegui la diagnostica, capacità del servizio web di test.

## <a name="see-also"></a>Vedere anche

 [SQL Server Machine Learning Services (In-Database)](sql-server-r-services.md)

