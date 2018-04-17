---
title: SQL Server di Machine Learning e R Services (In-Database) | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 24ef28cd5bfb8e09e3f0ac7dbfe46b5838ce029c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-machine-learning-and-r-services-in-database"></a>SQL Server di Machine Learning e R Services (In-Database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Un'installazione di nel database di machine learning opera all'interno del contesto di un'istanza del motore database SQL Server, fornendo il supporto di script esterni R e Python per i dati che si trovano nell'istanza di SQL Server. Poiché l'apprendimento è integrato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile mantenere analitica dati ed eliminare i costi e i rischi di protezione associati allo spostamento dei dati.

Poiché il motore di database multi-istanza, è possibile installare più istanze di analitica nel database, o anche meno recenti e più recenti versioni-by-side. Le opzioni includono uno [SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-standalone-windows-install.md) con R e Python, o [SQL Server 2016 R Services (In-Database)](../install/sql-r-standalone-windows-install.md) con appena R. 

I componenti di Machine learning possono anche essere installati come istanza indipendente [server autonomi](r-server-standalone.md). In genere, si consiglia di considerare (Standalone) e (In-Database) installazioni come si escludono a vicenda esclusivo per evitare il conflitto tra risorse, ma se si dispone di risorse sufficienti, non esistono alcun divieti contro installarli entrambi nello stesso computer fisico.

## <a name="choosing-between-in-database-and-standalone-analytics"></a>Scelta tra analitica nel database e da autonome

Comprendere i requisiti di sviluppo consente di scegliere tra (In-Database) e si avvicina (autonomo). Un server autonomo è più semplice da configurare e gestire se si desidera offrire la massima flessibilità nella modalità di utilizzo, o se si desidera inoltre connettersi a un'ampia gamma di origini dati all'esterno di SQL Server. 

Analitica nel database è progettati per l'integrazione completa con i dati all'interno di SQL Server. È possibile scrivere query T-SQL che chiamano funzioni R o Python ed eseguire lo script in SQL Server Management Studio o qualsiasi strumento o app usata per T-SQL esterno o incorporato. Se è necessario eseguire codice R o Python [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], utilizzando le stored procedure oppure utilizzando SQL Server l'istanza come il [contesto di calcolo](https://docs.microsoft.com/machine-learning-server/r/concept-what-is-compute-context), è necessario installare analitica nel database. Questa opzione offre la protezione dei dati massima e l'integrazione con strumenti di SQL Server.

Sia nel database e i server autonomi è possono tentare di risolvere i vincoli di memoria e l'elaborazione di R open source e Python. Entrambe le opzioni includono lo stesso pacchetti e gli strumenti, con la possibilità di caricare e di elaborare grandi quantità di dati su più core e aggregare i risultati in un singolo output consolidati. Le funzioni e gli algoritmi sono stati progettati per la scala e utilità: offrendo funzionalità analitica predittiva, modellazione statistica, le visualizzazioni dei dati e avanguardia algoritmi di machine learning in un prodotto server commerciale progettata e supportato da Microsoft. 

## <a name="components-of-an-in-database-installation"></a>Componenti di un'installazione di database

SQL Server 2016 è R. SQL Server 2017 supporta R e Python. Nella tabella seguente vengono descritte le funzionalità in ogni versione. Fatta eccezione per il servizio Launchpad di SQL Server, è identica a quello disponibile questa tabella la [articolo server autonomo](r-server-standalone.md).

| Componente | Description |
|-----------|-------------|
| Servizio Launchpad di SQL Server | Un servizio che gestisce le comunicazioni tra i runtime di R e Python esterni e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza. |
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

+ [SQL Server 2017 Machine Learning Services (In-Database)](../install/sql-machine-learning-services-windows-install.md)

+ [SQL Server 2016 R Services (In-Database) - R solo](../install/sql-r-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>Passaggio 2: Configurare uno strumento di sviluppo

Configurare gli strumenti di sviluppo per utilizzare i file binari del Server di Machine Learning. Per ulteriori informazioni su Python, vedere [i file binari Python collegamento](https://docs.microsoft.com/machine-learning-server/python/quickstart-python-tools). Per istruzioni su come connettersi in R Studio, vedere [usando versioni diverse di R](https://support.rstudio.com/hc/en-us/articles/200486138-Using-Different-Versions-of-R) e scegliere lo strumento C:\Program Files\Microsoft SQL Server\140\R_SERVER\bin\x64. È anche possibile provare [strumenti R per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation). 

Gli esperti di dati usano R o Python workstation i propri computer portatile o sviluppo, per esplorare i dati e di compilazione e ottimizzare i modelli predittivi fino a raggiungere un modello predittivo soddisfacente. 

Con analitica nel database in SQL Server, non è necessario modificare questo processo. Al termine dell'installazione, è possibile eseguire codice R o Python [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modalità locale o remota:

![rsql_keyscenario2](media/rsql-keyscenario2.png) 

+ **Usare l'IDE si preferisce**. I componenti client[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offrono tutti gli strumenti necessari all'esperto di dati per le attività di sperimentazione e sviluppo. Gli strumenti includono il runtime di R e la libreria del kernel matematico di Intel, che migliorano le prestazioni delle operazioni standard di R, oltre a un set di pacchetti R avanzati che supportano l'esecuzione del codice R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

+ **Lavorare in modalità remota o locale**. Come di consueto, gli esperti possono connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e aggiornare i dati nel client per l'analisi in locale. Tuttavia, una soluzione migliore consiste nell'utilizzare il **RevoScaleR** o **revoscalepy** le API per trasferire i calcoli per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer, evitando spostamenti costosi e non sicuri.

+ **Incorporare script R o Python in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure**. Quando il codice è completamente ottimizzato, eseguirne il wrapping in una stored procedure per evitare lo spostamento dei dati non necessari e ottimizzare le operazioni di elaborazione dati.

### <a name="step-3-write-your-first-script"></a>Passaggio 3: Scrivere lo script primo

Chiamare le funzioni R o Python all'interno dello script T-SQL:
  
  + [R: usare il codice R in Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md) 
  + [R: analisi nel database per sviluppatori SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)
  + [Python: Eseguire Python con T-SQL](../tutorials/run-python-using-t-sql.md)
  + [Python: analisi nel database per sviluppatori SQL](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Scegliere il linguaggio più adatto per l'attività. R è ideale per i calcoli statistici difficili da implementare con SQL. Per le operazioni sui dati basata su set, sfruttare la potenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ottenere prestazioni ottimali. Utilizzare il motore di database in memoria per i calcoli molto veloci su colonne.

### <a name="step-4-optimize-your-solution"></a>Passaggio 4: Ottimizzare la soluzione

Quando il modello è pronto per applicare la scalabilità ai dati aziendali, l'esperto di dati funziona spesso con lo sviluppatore di amministratore di database o SQL per ottimizzare i processi, ad esempio:

+ Progettazione delle funzionalità
+ Inserimento di dati e la trasformazione dei dati
+ Assegnazione dei punteggi

Gli esperti di dati con R sono sempre state problemi di prestazioni e scalabilità, soprattutto quando si utilizzano i dataset di grandi dimensioni. Ciò avviene perché l'implementazione di common runtime è a thread singolo e può gestire solo i set di dati che rientrano nella memoria disponibile nel computer locale. Integrazione con servizi di SQl Server Machine Learning fornisce più funzionalità per ottenere prestazioni migliori, con ulteriori dati:

+ **RevoScaleR**: R questo pacchetto contiene le implementazioni di alcune funzioni R più diffuse, riprogettate per garantire parallelismo e scalabilità. Il pacchetto include anche funzioni che incrementano scalabilità e prestazioni trasferendo i calcoli sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dotato in genere di più memoria e potenza di calcolo.

+ **revoscalepy**. Questa libreria Python, disponibile in SQL Server 2017, implementa funzioni più diffuse in RevoScaleR, ad esempio contesti di calcolo remoti e numerosi algoritmi che supportano l'elaborazione distribuita.

**Risorse**

+ [Case study sulle prestazioni](../../advanced-analytics/r/performance-case-study-r-services.md)
+ [R e ottimizzazione dei dati](../../advanced-analytics/r/r-and-data-optimization-r-services.md)

### <a name="step-5-deploy-and-consume"></a>Passaggio 5: Distribuire e usare

Quando lo script o il modello è pronto per la produzione, uno sviluppatore di database può incorporare il codice o il modello in una stored procedure, in modo che il codice Python o R salvato può essere chiamato da un'applicazione. L'archiviazione e l'esecuzione di codice R da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenta numerosi vantaggi: è possibile usare l'interfaccia intuitiva di [!INCLUDE[tsql](../../includes/tsql-md.md)] e tutti i calcoli avvengono nel database evitando spostamenti di dati non necessari.

![rsql_keyscenario1](media/rsql-keyscenario1.png)

+ **Sicuro ed estensibile**. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] Usa una nuova architettura di estendibilità che protegge il motore di database e isola le sessioni di R e Python. Consente inoltre di controllare gli utenti autorizzati a eseguire gli script, ed è possibile specificare quali database sono accessibili dal codice. È possibile controllare la quantità di risorse allocate al runtime, per evitare che calcoli grande da entità possano compromettere le prestazioni complessive del server.

+ **Pianificazione e controllo**. Se vengono eseguiti i processi di script esterni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile controllare e i dati di controllo utilizzato dagli esperti di dati. È inoltre possibile pianificare i processi e creare flussi di lavoro contenenti script R o Python esterni, esattamente come qualsiasi altro processo T-SQL o stored procedure, è consigliabile pianificare.

Per sfruttare i vantaggi delle funzionalità securty e gestione delle risorse in SQL Server, il processo di distribuzione potrebbe includere queste attività:

+ Conversione yourcode a una funzione che può eseguire in modo ottimale in una stored procedure
+ L'impostazione della sicurezza e il blocco di pacchetti utilizzati da un'attività specifica
+ L'abilitazione di governance delle risorse (richiede la versione Enterprise edition)

**Risorse**

+ [Governance delle risorse per R](resource-governance-for-r-services.md)
+ [Gestione dei pacchetti R per SQL Server](r-package-management-for-sql-server-r-services.md)

## <a name="see-also"></a>Vedere anche

 [SQL Server di Machine Learning e R Server (Standalone)](sql-server-r-services.md)
