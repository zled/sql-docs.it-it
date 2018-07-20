---
title: SQL Server Machine Learning e R Services (In-Database) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 05a2a17988912d7066b0d9f6bf398b889a3cd882
ms.sourcegitcommit: c37da15581fb34250d426a8d661f6d0d64f9b54c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39174778"
---
# <a name="sql-server-machine-learning-and-r-services-in-database"></a>SQL Server Machine Learning e R Services (In-Database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Un'installazione di in-database machine Learning opera all'interno del contesto di un'istanza del motore di database di SQL Server, fornendo il supporto di script esterni di R e Python per dati residenti nell'istanza di SQL Server. Perché machine learning è integrato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile mantenere analitica vicino ai dati ed eliminare i costi e rischi di sicurezza associati allo spostamento dei dati.

Poiché il motore di database è a istanza multipla, è possibile installare più istanze di analitica nel database, o anche meno recenti e più recenti versioni-by-side. Le scelte includono uno [SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-standalone-windows-install.md) con R e Python, o [SQL Server 2016 R Services (In-Database)](../install/sql-r-standalone-windows-install.md) con solo R. 

Componenti di apprendimento automatico possono anche essere installati come istanza indipendente [server autonomi](r-server-standalone.md). In generale, è consigliabile che considera (autonomo) e (In-Database) le installazioni come reciprocamente esclusivi per evitare conflitti di risorse, ma se si dispone di sufficienti risorse, non vi sono alcun divieti contro installarle entrambi nello stesso computer fisico.

## <a name="choosing-between-in-database-and-standalone-analytics"></a>Scelta tra analitica nel database e autonoma

Comprendere i requisiti di sviluppo consente di scegliere tra (In-Database) e si avvicina (autonomo). Un server autonomo è più semplice configurare e gestire se si desidera che la massima flessibilità nella modalità di utilizzo, o se si vuole anche connettersi a un'ampia gamma di origini dati all'esterno di SQL Server. 

Analitica nel database è progettati per una profonda integrazione con i dati all'interno di SQL Server. È possibile scrivere query T-SQL che chiamano funzioni R o Python ed eseguire lo script in SQL Server Management Studio o qualsiasi strumento o l'app usata per T-SQL incorporato o esterno. Se è necessario eseguire codice R o Python [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzando le stored procedure oppure con SQL Server l'istanza come il [contesto di calcolo](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context), è necessario installare analitica nel database. Questa opzione offre la protezione dei dati massima e l'integrazione con strumenti di SQL Server.

Sia nel database e i server autonomi, si eviteranno i vincoli di memoria e l'elaborazione di R e Python open source. Entrambe le opzioni includono gli stessi pacchetti e strumenti, con la possibilità di caricare ed elaborare grandi quantità di dati su più core e aggregare i risultati in un singolo output consolidato. Le funzioni e gli algoritmi sono progettati per operare sia scalabilità che utilità: recapito di analitica predittiva, modellazione statistica, visualizzazioni dei dati e avanguardia algoritmi di machine learning in un prodotto commerciale server progettato e supportato da Microsoft. 

## <a name="components-of-an-in-database-installation"></a>Componenti di un'installazione di nel database

SQL Server 2016 è solo R. SQL Server 2017 supporta R e Python. La tabella seguente descrive le funzionalità di ogni versione. Fatta eccezione per il servizio Launchpad di SQL Server, è identica a quello disponibile questa tabella la [articolo su server autonomi](r-server-standalone.md).

| Componente | Description |
|-----------|-------------|
| Servizio Launchpad di SQL Server | Un servizio che gestisce le comunicazioni tra i runtime di R e Python esterni e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza. |
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

+ [SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md)

+ [SQL Server 2016 R Services (In-Database) - solo R](../install/sql-r-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>Passaggio 2: Configurare uno strumento di sviluppo

Configurare gli strumenti di sviluppo per usare i file binari di Machine Learning Server. Per altre informazioni su Python, vedere [i file binari Python collegamento](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Per istruzioni su come connettersi in R Studio, vedere [con diverse versioni di R](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) e scegliere lo strumento C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64. È inoltre possibile tentare [R Tools per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation). 

I data Scientist usano in genere R o Python nella workstation propri computer portatili o di sviluppo, per esplorare i dati, sviluppare e ottimizzare i modelli predittivi fino a raggiungere un modello predittivo soddisfacente. 

Con analitica nel database in SQL Server, non è necessario modificare questo processo. Al termine dell'installazione, è possibile eseguire codice R o Python [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale o remota:

![rsql_keyscenario2](media/rsql-keyscenario2.png) 

+ **Usare l'IDE si preferisce**. I componenti client[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offrono tutti gli strumenti necessari all'esperto di dati per le attività di sperimentazione e sviluppo. Gli strumenti includono il runtime di R e la libreria del kernel matematico di Intel, che migliorano le prestazioni delle operazioni standard di R, oltre a un set di pacchetti R avanzati che supportano l'esecuzione del codice R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

+ **Lavorare in remoto o in locale**. Come di consueto, gli esperti possono connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e aggiornare i dati nel client per l'analisi in locale. Tuttavia, una soluzione migliore consiste nell'usare la **RevoScaleR** o **revoscalepy** API per trasferire i calcoli di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer, evitando spostamenti costosi e non sicuri.

+ **Incorporare script R o Python nella [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure**. Quando il codice è perfettamente ottimizzato, eseguirne il wrapping in una stored procedure per evitare lo spostamento dei dati non necessari e ottimizzare le attività di elaborazione dei dati.

### <a name="step-3-write-your-first-script"></a>Passaggio 3: Scrivere il primo script

Chiamare funzioni R o Python dall'interno di uno script T-SQL:
  
  + [R: usare il codice R in Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md) 
  + [R: analisi nel database per sviluppatori SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)
  + [Python: Eseguire Python con T-SQL](../tutorials/run-python-using-t-sql.md)
  + [Python: analisi nel database per sviluppatori SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Scegliere il linguaggio migliore per l'attività. R è ideale per i calcoli statistici difficili da implementare tramite SQL. Per le operazioni sui dati basata su set sfrutta la potenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ottenere prestazioni ottimali. Usare il motore di database in memoria per i calcoli molto veloci su colonne.

### <a name="step-4-optimize-your-solution"></a>Passaggio 4: Ottimizzare la soluzione

Quando il modello è pronto per la scalabilità su dati aziendali, il data scientist spesso funziona con lo sviluppatore di amministratore di database o SQL per ottimizzare i processi, ad esempio:

+ Progettazione delle funzionalità
+ L'inserimento di dati e trasformazione dei dati
+ Assegnazione dei punteggi

In genere i data Scientist usano R hanno avuto problemi con le prestazioni e scalabilità, soprattutto quando si utilizzano set di dati di grandi dimensioni. Ciò avviene perché l'implementazione di common runtime è a thread singolo e può gestire solo i set di dati che rientrano nella memoria disponibile nel computer locale. Integrazione con servizi di SQl Server Machine Learning offre molte funzionalità per ottenere prestazioni migliori, più dati:

+ **RevoScaleR**: R questo pacchetto contiene le implementazioni di alcune delle funzioni R più diffuse, riprogettate per garantire parallelismo e scalabilità. Il pacchetto include anche funzioni che incrementano scalabilità e prestazioni trasferendo i calcoli sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dotato in genere di più memoria e potenza di calcolo.

+ **revoscalepy**. Questa libreria di Python, disponibile in SQL Server 2017 implementa funzioni più diffuse in RevoScaleR, ad esempio contesti di calcolo remoti e molti algoritmi che supportano l'elaborazione distribuita.

**Risorse**

+ [Case study sulle prestazioni](../../advanced-analytics/r/performance-case-study-r-services.md)
+ [R e ottimizzazione dei dati](../../advanced-analytics/r/r-and-data-optimization-r-services.md)

### <a name="step-5-deploy-and-consume"></a>Passaggio 5: Distribuire e usare

Dopo lo script o il modello è pronto per la produzione, uno sviluppatore di database può incorporare il codice o il modello in una stored procedure, in modo che il codice R o Python salvato può essere chiamato da un'applicazione. L'archiviazione e l'esecuzione di codice R da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenta numerosi vantaggi: è possibile usare l'interfaccia intuitiva di [!INCLUDE[tsql](../../includes/tsql-md.md)] e tutti i calcoli avvengono nel database evitando spostamenti di dati non necessari.

![rsql_keyscenario1](media/rsql-keyscenario1.png)

+ **Sicuro ed estensibile**. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] Usa una nuova architettura di estendibilità che protegge il motore di database e isola le sessioni di R e Python. Anche possibile gestire gli utenti autorizzati a eseguire gli script ed è possibile specificare i database che sono accessibili dal codice. È possibile controllare la quantità di risorse allocate al runtime, per evitare che calcoli di grande da entità possano compromettere le prestazioni complessive del server.

+ **Pianificazione e il controllo**. Se vengono eseguiti i processi di script esterni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile controllare e controlla i dati usati dai data Scientist. È inoltre possibile pianificare i processi e creare flussi di lavoro contenenti script R o Python esterni, esattamente come qualsiasi altro processo T-SQL o stored procedure, è consigliabile pianificare.

Per sfruttare i vantaggi delle funzionalità securty e gestione delle risorse in SQL Server, il processo di distribuzione può includere queste attività:

+ Conversione yourcode a una funzione che è possibile eseguire in modo ottimale in una stored procedure
+ L'impostazione della sicurezza e blocco dei pacchetti utilizzati da un'attività specifica
+ Abilitazione della governance delle risorse (richiede la versione Enterprise edition)

**Risorse**

+ [Governance delle risorse per R](resource-governance-for-r-services.md)
+ [Gestione dei pacchetti R per SQL Server](install-additional-r-packages-on-sql-server.md)

## <a name="see-also"></a>Vedere anche

 [SQL Server Machine Learning e R Server (Standalone)](sql-server-r-services.md)
