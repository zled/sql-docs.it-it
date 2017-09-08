---
title: "Le differenze nelle funzionalità di machine learning tra le edizioni di SQL Server | Documenti Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b33a3e2-04d3-4bad-9335-9568ae09db0b
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9b520b7fc7e97498f4b46a43ad991558025123a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---

# <a name="differences-in-machine-learning-features-between-editions-of-sql-server"></a>Differenze nelle funzionalità di machine learning tra le edizioni di SQL Server
 
 Supporto per machine learning è disponibile nelle seguenti edizioni di SQL Server 2016 e SQL Server 2017:

## <a name="summary-of-differences"></a>Riepilogo delle differenze

-   **Enterprise Edition**
    
     SQL Server 2017 include servizi di Machine Learning (nel database. SQL Server 2016 include i servizi di R. Questa funzionalità supporta analitica nel database in SQL Server, incluso l'utilizzo di SQL Server come un contesto di calcolo.
     
     SQL Server 2017 include Microsoft Machine Learning Server (Standalone). SQL Server 2016 include Microsoft R Server (Standalone). Questa funzionalità supporta rendere operativo il machine learning che non richiede l'utilizzo di SQL Server come un contesto di calcolo.

     Non sono previste restrizioni su queste funzionalità in Enterprise Edition, che offre prestazioni ottimizzate e scalabilità tramite la parallelizzazione e lo streaming. Inoltre, questa edizione massimizza l'uso di supporto della piattaforma per l'esecuzione del flusso e parallela.
     
     Analitica nel database utilizzando SQL Server supporta la governance delle risorse di script esterni per personalizzare l'utilizzo di risorse server.
     
     Versioni più recenti di Microsoft R Server includono una versione migliorata del motore di rendere operativo che supporta la distribuzione rapida e sicura e condivisione di soluzioni R. Per ulteriori informazioni, vedere [mrsdeploy](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package).

-   **Developer Edition**

     Stesse funzionalità di Enterprise Edition. Developer Edition tuttavia non può essere usata negli ambienti di produzione.  
  
-   **Standard Edition**

     Tutte le funzionalità di analitica nel database include con Enterprise Edition, ad eccezione di governance delle risorse. Prestazioni e la scala è limitata: i dati che possono essere elaborati devono essere contenuta nella memoria del server e l'elaborazione è limitata a un thread singolo calcolo, anche quando si usa il **RevoScaleR** funzioni.
  
-   **Express Edition e Web Edition**
  
     Solo Express Edition with Advanced Services include di machine learning funzionalità. Le limitazioni delle prestazioni sono simili a quelle di Standard Edition. Edizione Web non è per attività quali la creazione di modelli di machine learning; Tuttavia, è possibile utilizzare la funzione di stima per eseguire l'assegnazione dei punteggi usando i modelli di training in un' posizione.

-   **Database SQL di Azure**
  
     Funzionalità di apprendimento macchina, ad esempio R e Python script non sono attualmente supportate in Database SQL di Azure.
     
     Per ulteriori informazioni e annunci sugli quando la funzionalità specificata sarà disponibile, vedere il blog di SQL Server: [Python in SQL Server 2017: avanzato nel database machine learning](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)


### <a name="languages-supported-in-all-editions"></a>Lingue supportate in tutte le edizioni

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

Developer Edition offre prestazioni equivalenti a quelle di Enterprise Edition. L'uso di Developer Edition non è tuttavia supportato per gli ambienti di produzione.

## <a name="machine-learning-in-standard-edition"></a>Machine learning in Standard Edition

Anche Standard Edition dovrebbe offrire alcuni vantaggi in termini di prestazioni, rispetto ai pacchetti R standard, a parità di configurazione hardware.

Standard Edition non supporta Resource Governor. Utilizzo di governance delle risorse è il modo migliore per personalizzare le risorse del server per supportare diversi carichi di lavoro come modello di training e assegnazione dei punteggi.

Standard Edition offre anche prestazioni e scalabilità limitate rispetto alle edizioni Enterprise e Developer. Tutti i **RevoScaleR** pacchetti e le funzioni sono inclusi con l'edizione Standard, ma è limitato il numero di processi è possibile usare il servizio che avvia e gestisce gli script R. I dati elaborati dallo script devono inoltre rientrare nella memoria.  Le stesse restrizioni si applicano alle soluzioni che utilizzano **revoscalepy**.

## <a name="machine-learning-in-express-edition-with-advanced-services"></a>Machine learning in Express Edition with Advanced Services

Express Edition è soggetta alle stesse limitazioni di Standard Edition.

## <a name="machine-learning-in-web-edition"></a>Machine learning in Web Edition

Web edition non supporta l'esecuzione di script R o Python. Tuttavia, è possibile utilizzare la funzione di stima per eseguire [punteggio native](../sql-native-scoring.md) su un modello che è stato eseguito il training in un'istanza diversa di SQL Server o Server di R e quindi salvato in formato binario richiesto.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, vedere:

+ [Edizioni e componenti di SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [Edizioni e componenti di SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md)

Per ulteriori informazioni su altre funzionalità di SQL Server, vedere:

+ [Edizioni e funzionalità supportate per SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md) 

Per ulteriori informazioni sulle funzionalità di Microsoft R e come è possibile ottimizzare la soluzione per grandi set di dati, vedere il [Microsoft R Server](https://docs.microsoft.com/r-server/r/tutorial-large-data-tips) documentazione.
