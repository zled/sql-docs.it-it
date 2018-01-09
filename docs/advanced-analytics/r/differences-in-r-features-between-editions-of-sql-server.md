---
title: "Le differenze nelle funzionalità di machine learning tra le edizioni di SQL Server | Documenti Microsoft"
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
caps.latest.revision: "12"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 839f9fbb2216a153ce1171f57e4021d9c0a43544
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="differences-in-machine-learning-features-between-editions-of-sql-server"></a>Differenze nelle funzionalità di machine learning tra le edizioni di SQL Server
 
 Supporto per machine learning è disponibile in SQL Server 2016 e SQL Server 2017. In questo articolo sono elencate le edizioni che supportano la funzionalità, vengono descritte le limitazioni aggiuntive che si applicano in edizioni specifiche e vengono elencate le funzionalità disponibili solo in alcune edizioni.

 > [!NOTE]
 > In generale, SQL Server Machine Learning non include il [rendere operativo il](https://docs.microsoft.com/machine-learning-server/what-is-operationalization) funzionalità incluse in Microsoft R Server o Server di Machine Learning.
 > 
 > Se è necessario queste funzionalità, è possibile installare Microsoft R Server o Server di Machine Learning separatamente, per supportare la distribuzione di modelli predittivi come servizio web. 

## <a name="summary-of-differences"></a>Riepilogo delle differenze

-   **Enterprise Edition**
    
     SQL Server 2017 include servizi di Machine Learning (nel database. SQL Server 2016 include i servizi di R. Questa funzionalità supporta analitica nel database in SQL Server, incluso l'utilizzo di SQL Server come un contesto di calcolo.
     
     SQL Server 2017 include Microsoft Machine Learning Server (Standalone). SQL Server 2016 include Microsoft R Server (Standalone). Questa funzionalità supporta rendere operativo il machine learning che non richiede l'utilizzo di SQL Server come un contesto di calcolo.

     Non sono previste restrizioni su queste funzionalità in Enterprise Edition, che offre prestazioni ottimizzate e scalabilità tramite la parallelizzazione e lo streaming. Inoltre, questa edizione massimizza l'uso di supporto della piattaforma per l'esecuzione del flusso e parallela. Ciò significa che, a differenza di Standard Edition, i dati di input non deve superare la memoria, ma può essere trasmesso.
     
     Analitica nel database utilizzando SQL Server supporta la governance delle risorse di script esterni per personalizzare l'utilizzo di risorse server.
     
     Le versioni più recenti di Microsoft R Server e Server di Machine Learning includono una versione migliorata del motore di rendere operativo che supporta la distribuzione rapida e sicura e condivisione di soluzioni R. Per ulteriori informazioni, vedere [rendere operative le analitica con Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-operationalization).

-   **Developer Edition**

     Stesse funzionalità di Enterprise Edition. Developer Edition tuttavia non può essere usata negli ambienti di produzione.  
  
-   **Standard Edition**

     Tutte le funzionalità di analitica nel database include con Enterprise Edition, ad eccezione di governance delle risorse. Prestazioni e scalabilità sono limitati: i dati che possono essere elaborati devono essere contenuta nella memoria del server e l'elaborazione è limitata a un thread singolo calcolo, anche quando si usa il **RevoScaleR** funzioni.
  
-   **Express Edition e Web Edition**
  
     Solo Express Edition with Advanced Services include di machine learning funzionalità. Le limitazioni delle prestazioni sono simili a quelle di Standard Edition. 
     
     Web Edition non è per attività quali la creazione di modelli di machine learning. Tuttavia, è possibile utilizzare la funzione di stima per eseguire l'assegnazione dei punteggi usando i modelli di training in un' posizione.

-   **Database SQL di Azure**
  
     Dopo una versione di prova iniziale è attualmente R Services **non** disponibili nel Database di SQL Azure, in attesa di ulteriore sviluppo. 

### <a name="external-script-languages-supported"></a>Linguaggi di script esterni supportati

Per tutte le edizioni, sono supportate le seguenti lingue di machine learning:

+ SQL Server 2017: R e Python
+ SQL Server 2016: R solo

Microsoft R Open è incluso in tutte le edizioni.

Microsoft R Client può utilizzare tutte le edizioni.

## <a name="machine-learning-in-enterprise-edition"></a>Machine learning in Enterprise Edition

Prestazioni delle soluzioni di machine learning in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è previsto che in genere superano le implementazioni con R convenzionale assegnato lo stesso hardware. Che dipende dal fatto che in SQL Server, è possono eseguire soluzioni R usando risorse del server e talvolta distribuite a più processi mediante il **RevoScaleR** funzioni. 

Le prestazioni non sono stata valutata per le soluzioni di Python, come la funzionalità è ancora in fase di sviluppo, ma è previsto un alcuni dei vantaggi offerti da applicare.

Gli utenti possono prevedere anche visualizzare le differenze notevoli nelle prestazioni e scalabilità nella stessa soluzione di machine learning se eseguito in Visual Studio Enterprise Edition. Standard Edition. Motivi includono il supporto per parallel l'elaborazione, aumentare i thread disponibili per machine learning e streaming (o la suddivisione in blocchi), che consente le funzioni RevoScaleR gestire più dati possono adattarsi alla memoria. 

Tuttavia, può influire sulle prestazioni anche nello stesso hardware da molti fattori all'esterno del codice R o Python. Questi fattori sulle richieste di risorse del server, il tipo di piano di query che viene creato, le modifiche dello schema, la necessità di aggiornare le statistiche o creare un nuovo piano di query, la frammentazione e altro ancora. È possibile che una stored procedure contenente il codice R o Python potrebbero essere eseguiti in secondi sotto un carico di lavoro, ma richiedere minuti se sono presenti altri servizi in esecuzione.  È pertanto consigliabile monitorare più aspetti di prestazioni del server, tra cui la rete per contesti di calcolo remoto, durante la misurazione delle prestazioni di machine learning.

È inoltre consigliabile configurare [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) (disponibile nell'edizione Enterprise) per personalizzare la modalità che i processi di script esterni vengono ordinati in o gestiti in carichi di lavoro elevato sul server. È possibile definire le funzioni di classificazione per specificare l'origine del processo dello script esterno e stabilire le priorità di alcuni carichi di lavoro, limitare la quantità di memoria utilizzata dalle query SQL e controllare il numero di processi paralleli consente l'utilizzo del carico di lavoro.

## <a name="machine-learning-in-developer-edition"></a>Machine learning in Developer Edition

Developer Edition offre prestazioni equivalente a quella dell'edizione Enterprise.

Utilizzo di Developer Edition non è supportato per gli ambienti di produzione.

## <a name="machine-learning-in-standard-edition"></a>Machine learning in Standard Edition

Anche Standard Edition dovrebbe offrire alcuni vantaggi in termini di prestazioni, rispetto ai pacchetti R standard, a parità di configurazione hardware.

Standard Edition non supporta Resource Governor. Standard Edition fornisce inoltre limitazione delle prestazioni e scalabilità rispetto a Enterprise Edition e Developer Edition.

Tutti i **RevoScaleR** pacchetti e le funzioni sono inclusi con l'edizione Standard, ma è limitato il numero di processi è possibile usare il servizio che avvia e gestisce gli script R. I dati elaborati dallo script devono inoltre rientrare nella memoria.

Le stesse restrizioni si applicano alle soluzioni che utilizzano **revoscalepy**.

## <a name="machine-learning-in-express-edition-with-advanced-services"></a>Machine learning in Express Edition with Advanced Services

Express Edition è soggetta alle stesse limitazioni di Standard Edition.

## <a name="machine-learning-in-web-edition"></a>Machine learning in Web Edition

Web edition non supporta l'esecuzione di script R o Python. Tuttavia, è possibile utilizzare il [PREDICT](../../t-sql/queries/predict-transact-sql.md) funzione per eseguire [punteggio native](../sql-native-scoring.md) su un modello che è stato eseguito il training in un'istanza diversa di SQL Server o Server di R e quindi salvato in formato binario richiesto.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, vedere:

+ [Edizioni e componenti di SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [Edizioni e componenti di SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md)

Per ulteriori informazioni su altre funzionalità di SQL Server, vedere:

+ [Edizioni e le funzionalità supportate di SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md) 

Per ulteriori informazioni su come ottimizzare la soluzione per grandi set di dati, vedere [suggerimenti per l'elaborazione dati di grandi dimensioni in R](https://docs.microsoft.com/machine-learning-server/r/tutorial-large-data-tips) documentazione.
