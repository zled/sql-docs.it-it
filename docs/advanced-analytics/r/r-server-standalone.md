---
title: Machine Learning Server (Standalone) di SQL Server e R Server (Standalone) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 06/22/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
vms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.openlocfilehash: 3f6bb60e639517e458684486f36123d47a68dbf9
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="sql-server-machine-learning-server-standalone-and-r-server-standalone"></a>Machine Learning Server (Standalone) di SQL Server e R Server (Standalone)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Un server autonomo è un'installazione dei componenti di machine learning, articolato come funzioni R e Python, eseguite in modo indipendente da istanze del motore di database SQL Server. È possibile installare un server autonomo autonomamente, senza dipendenze in SQL Server. Poiché un server autonomo è indipendente dell'attività di SQL Server, configurazione e amministrazione e gli strumenti sono più simili a una versione non SQL del Server di apprendimento macchina, che è possibile leggere nella [in questo articolo](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server).

L'obiettivo di server autonomo machine learning consiste nel fornire un ambiente di sviluppo completo, con l'elaborazione distribuita e parallela dei carichi di lavoro di R e Python in piccole per grandi set di dati, utilizzando i pacchetti proprietari e motori di calcolo installato con il server. I pacchetti R e Python in un server autonomo sono identici a quelli forniti in un'installazione di SQL Server (In-Database), consentendo la portabilità del codice e [cambio di contesto di calcolo](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context).

Gli sviluppatori di motivo principale scelgono che server autonomo machine learning consiste nello spostare oltre i vincoli di memoria e l'elaborazione di R open source e Python. I server autonomi possono caricare ed elaborare grandi quantità di dati su più core e aggregare i risultati in un singolo output consolidati. Le funzioni e gli algoritmi sono stati progettati per la scala e utilità: offrendo funzionalità analitica predittiva, modellazione statistica, le visualizzazioni dei dati e avanguardia algoritmi di machine learning in un prodotto server commerciale progettata e supportato da Microsoft.

In genere, si consiglia di considerare (Standalone) e (In-Database) le installazioni come si escludono a vicenda per evitare il conflitto tra risorse, ma se si dispone di risorse sufficienti, non è non divieto di installarli entrambi nello stesso computer fisico.

Può avere solo un server autonomo nel computer: uno [Machine Learning Server (standalone) di SQL Server 2017](../install/sql-machine-learning-standalone-windows-install.md) oppure [SQL Server 2016 R Server (Standalone)](../install/sql-r-standalone-windows-install.md). Prima di installare una versione diversa, è necessario disinstallare manualmente una versione.

## <a name="components-of-a-standalone-server"></a>Componenti di un server autonomo

SQL Server 2016 è R. SQL Server 2017 supporta R e Python. Nella tabella seguente vengono descritte le funzionalità in ogni versione.

| Componente | Description |
|-----------|-------------|
| Pacchetti R | [RevoScaleR](revoscaler-overview.md) è la libreria primaria per R scalabili con le funzioni per la manipolazione dei dati, trasformazione, visualzation e analisi.  <br/>[MicrosoftML (R)](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) aggiunge algoritmi di machine learning per creare modelli personalizzati per l'analisi del testo, analisi delle immagini e analisi del sentiment. <br/>[mrsdeploy](operationalization-with-mrsdeploy.md) offerte web distribuzione del servizio (in SQL Server 2017 solo). <br/>[olapR](how-to-create-mdx-queries-using-olapr.md) consente di specificare le query MDX in R.|
| Microsoft R Open (MRO) | [MRO](https://mran.microsoft.com/open) la distribuzione di Microsoft open source di R. Il pacchetto e l'interprete sono inclusi. Utilizzare sempre la versione di MRO in bundle nel programma di installazione. |
| Strumenti di R | Prompt dei comandi e finestre della console di R sono strumenti standard in una distribuzione di R. \Programmi\Microsoft SQL Server\140\R_SERVER\bin\x64 sono disponibili tramite. |
| Esempi di R e gli script |  Pacchetti open source di R e RevoScaleR includono set di dati incorporato in modo che è possibile creare ed eseguire script utilizzando i dati pre-installati. Cercarli in \Programmi\Microsoft SQL Server\140\R_SERVER\library\datasets e \library\RevoScaleR. |
| Pacchetti di Python | [revoscalepy](../python/what-is-revoscalepy.md) è la libreria primaria per Python scalabile con le funzioni per la manipolazione dei dati, trasformazione, visualzation e analisi. <br/>[microsoftml (Python)](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) aggiunge algoritmi di machine learning per creare modelli personalizzati per l'analisi del testo, analisi delle immagini e analisi del sentiment.  |
| Strumenti Python | Lo strumento da riga di comando Python incorporato è utile per test ad hoc e attività. Trova lo strumento in \Programmi\Microsoft SQL Server\140\PYTHON_SERVER\python.exe. |
| Anaconda | Anaconda è una distribuzione open source di Python e pacchetti essenziali. |
| Script e gli esempi di Python | A R, Python include set di dati incorporato e script. Trovare i dati revoscalepy \Programmi\Microsoft SQL Server\140\PYTHON_SERVER\lib\site-packages\revoscalepy\data\sample-data. |
| Modelli con training preliminare in R e Python | I modelli con training preliminare sono supportati e può essere usato in un server autonomo, ma è possibile installare questi componenti tramite il programma di installazione di SQL Server. Il programma di installazione per il Server di Microsoft Machine Learning fornisce i modelli, è possibile installare gratuitamente. Per altre informazioni, vedere [Install pretrained modelli di machine learning in SQL Server](install-pretrained-models-sql-server.md). |

## <a name="get-started-step-by-step"></a>Introduzione dettagliata

Avviare l'installazione, collegare i file binari per uno strumento di sviluppo preferito e scrivere lo script primo.

### <a name="step-1-install-the-software"></a>Passaggio 1: Installare il software

Installare una di queste versioni:

+ [SQL Server 2017 Machine Learning Server (standalone)](../install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Server (Standalone) - R solo](../install/sql-r-standalone-windows-install.md)

### <a name="step-2-configure-a-development-tool"></a>Passaggio 2: Configurare uno strumento di sviluppo

Configurare gli strumenti di sviluppo per utilizzare i file binari del Server di Machine Learning. Per ulteriori informazioni su Python, vedere [i file binari Python collegamento](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Per istruzioni su come connettersi in R Studio, vedere [usando versioni diverse di R](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) e scegliere lo strumento C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64. È anche possibile provare [strumenti R per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation). 

### <a name="step-3-write-your-first-script"></a>Passaggio 3: Scrivere lo script primo

Scrivere script R o Python utilizzando le funzioni da RevoScaleR revoscalepy e di algoritmi di machine learning.
  
  + [Esplorare R e RevoScaleR nelle 25 funzioni](https://docs.microsoft.com/machine-learning-server/r/tutorial-r-to-revoscaler): iniziano con i comandi di base R e quindi lo stato di avanzamento per le funzioni analitiche distribuibile RevoScaleR che offrono prestazioni elevate e scalabilità per soluzioni R. Include versioni parallelizzabili di molti dei più diffusi pacchetti di modellazione R, tra cui clustering K-Means, alberi delle decisioni e foreste delle decisioni, nonché strumenti per la modifica dei dati.

  + [Guida introduttiva: Un esempio di classificazione binaria con il pacchetto di Python microsoftml](https://docs.microsoft.com/machine-learning-server/python/quickstart-binary-classification-with-microsoftml): creare un modello di classificazione binaria usando le funzioni da microsoftml e noto esempio breast cancer dataset.

Scegliere il linguaggio più adatto per l'attività. R è ideale per i calcoli statistici difficili da implementare con SQL. Per le operazioni sui dati basata su set, sfruttano la potenza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ottenere prestazioni ottimali. Utilizzare il motore di database in memoria per i calcoli molto veloci applicati alle colonne.

### <a name="step-4-operationalize-your-solution"></a>Passaggio 4: Sincerarmi la soluzione

Server autonomi è possono usare il [rendere operativo](https://docs.microsoft.com//machine-learning-server/what-is-operationalization) funzionalità di senza SQL-personalizzazione [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server). È possibile configurare un server autonomo per rendere operativo, che offre i seguenti vantaggi: distribuire e ospitare il codice come servizi web, Esegui la diagnostica, verificare la capacità del servizio web.

## <a name="see-also"></a>Vedere anche

 [SQL Server apprendimento Services (In-Database)](sql-server-r-services.md)

