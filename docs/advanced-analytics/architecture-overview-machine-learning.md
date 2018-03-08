---
title: Panoramica dell'architettura di servizi di SQL Server Machine Learning | Documenti Microsoft
ms.custom: 
ms.date: 11/03/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 4272a0f421bc8286fc9be7be44e3b7ef8cc13905
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="architecture-overview-for-sql-server-machine-learning-services"></a>Panoramica dell'architettura di servizi di SQL Server Machine Learning 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo argomento descrive gli obiettivi di framework di estendibilità che supporta l'esecuzione dello script Python e R in SQL Server.

Fornisce inoltre una panoramica di come l'architettura è progettata per soddisfare questi obiettivi, come vengono supportati ed eseguire da SQL Server e i vantaggi di integrazione R e Python.

In generale, il framework di estendibilità è quasi identico per R e Python, con alcune piccole differenze dei dettagli di avvio che viene chiamati, le opzioni di configurazione e così via. Per ulteriori informazioni sull'implementazione per una lingua specifica, vedere questi argomenti:

- [Panoramica dell'architettura per SQL Server R Services](r/architecture-overview-sql-server-r.md)
- [Panoramica dell'architettura per Python in SQL Server](python/architecture-overview-sql-server-python.md)


## <a name="background"></a>Informazioni preliminari

In SQL Server 2016, sono state introdotte numerose modifiche al motore di database per supportare l'esecuzione di script R con SQL Server. In SQL Server 2017, questa infrastruttura sottostante è stata migliorata per aggiungere il supporto per la lingua di Python.

È stata l'obiettivo del framework di estensibilità per creare un'interfaccia tra SQL Server e linguaggi di analisi scientifica dei dati, ad esempio R e Python, per ridurre ulteriormente l'attrito correlato che si verifica quando le soluzioni di analisi scientifica dei dati vengono spostate nell'ambiente di produzione e per proteggere i dati che potrebbero essere migliorata esposto durante il processo di sviluppo dell'analisi scientifica dei dati.

Tramite l'esecuzione di un linguaggio di scripting attendibile all'interno di un framework sicuro gestito da SQL Server, lo sviluppatore del database può garantire la sicurezza, consentendo di esperti di dati utilizzare i dati dell'organizzazione.

  ![Obiettivi dell'integrazione con SQL Server](media/ml-service-value-add.png "Machine Learning servizi a valore aggiunto")

- Gli utenti correnti di R o Python devono essere in grado di convertire il codice ed eseguirlo in SQL Server con le modifiche di lieve.
- Il modello di protezione dati in SQL Server viene esteso ai dati utilizzati dai linguaggi di script esterni. In altre parole, un utente che esegue uno script R o Python non deve essere in grado di utilizzare tutti i dati non è stato possibile accedere da tale utente in una query SQL.
- L'amministratore del database deve essere in grado di gestire le risorse usate da script esterni, gestire gli utenti, gestire e monitorare le librerie di codice esterno.
- Il sistema deve supportare soluzioni basate interamente sui distribuzioni Apri origine di R e Python, ma utilizzare proprietari componenti sviluppati da Microsoft per fornire maggiore sicurezza e prestazioni.

## <a name="architecture-core-concepts"></a>Concetti di base di architettura

Per soddisfare questi obiettivi, l'architettura di SQL Server 2016 R Services e i servizi SQL Server 2017 Machine Learning per R e Python è basata su questi concetti di base:

+ **Architettura multiprocesso**

  R sia Python sono le lingue con supporto avanzato ed entusiasti della community open source. Pertanto, è importante mantenere completa interoperabilità con R open source e Python.

  Apri origine distribuzioni di R e Python vengono installate con SQL Server con licenza e possono funzionare in modo indipendente da SQL Server se necessario.

   Inoltre, Microsoft fornisce un set di librerie proprietarie che consentono l'integrazione con SQL Server, incluse la conversione dei dati, la compressione e dell'ottimizzazione destinata a ogni lingua supportata.

+ **Sicurezza**

   Migliora la sicurezza significa supporto per autenticazione integrata di Windows sia basata su password account di accesso SQL, come la gestione e la protezione delle credenziali, per la protezione dei dati e l'uso di SQL Server Trusted Launchpad per la gestione di script esterni vengono usati in SQL Server l'esecuzione e la protezione dei dati utilizzati negli script.

+ **Scalabilità e prestazioni**

  Integrazione con SQL Server è essenziale per migliorare l'utilità di R e Python nell'organizzazione. È possibile eseguire uno script R o Python chiamando una stored procedure e i risultati vengono restituiti come risultati tabulari direttamente a SQL Server, semplificando di generare o utilizzare l'apprendimento da qualsiasi applicazione in grado di inviare una query SQL e gestire i risultati.

  Ottimizzazione delle prestazioni si basa su due aspetti altrettanto efficaci della piattaforma: la governance delle risorse e parallelo utilizzando SQL Server di elaborazione e distributed computing fornite da algoritmi nel **RevoScaleR** e **revoscalepy**.

## <a name="solution-development-and-deployment"></a>Distribuzione e lo sviluppo di soluzioni

Oltre a questi obiettivi di base per la piattaforma di estendibilità, i servizi di machine learning in SQL Server sono progettati per fornire l'integrazione avanzata con il motore di database e lo stack di Business Intelligence, con i seguenti vantaggi:

+ Gestione delle risorse e delle prestazioni tramite gli strumenti di monitoraggio tradizionale
+ Semplice utilizzo dei dati di Python e R da gruppi di BI o qualsiasi applicazione in grado di utilizzare i risultati della query SQL
+ Quantità barriera inferiore per lo sviluppo di soluzioni di machine learning enterprise

Di seguito viene illustrato come funziona in pratica.

  ![Processo di sviluppo di soluzioni ML](media/ml-solution-development-process.png "sviluppare e distribuire usando servizi di Machine Learning")

1. I dati vengono mantenuti all'interno del limite di conformità e utilizzo dei dati può essere gestito e monitorato da SQL Server. Nel frattempo, l'amministratore di database ha il pieno controllo su chi può installare i pacchetti o eseguire script nel server. Se lo si desidera, l'amministratore di database può inoltre in grado di delegare le autorizzazioni a livello di database per gli esperti di dati o i gestori.
2. Gli esperti di dati possano compilare e testare soluzioni nei propri ambienti di R o Python Preferiti, disconnessi dal server.
3. Gli sviluppatori di SQL è possono utilizzare strumenti familiari, ad esempio Management Studio o Visual Studio per integrare il codice R o Python con SQL Server. Una stretta integrazione significa che lo sviluppatore esperti possa scegliere lo strumento migliore per ottimizzare ogni attività. Ad esempio, è possibile utilizzare SQL per alcune attività di progettazione di funzionalità e i R ad altri utenti. Si potrebbe incorporare script Python in un'attività di Integration Services per eseguire analitica testo sofisticate.
4. Testata e pronti per distribuire le soluzioni possono essere ottimizzate tramite tecnologie di SQL Server, ad esempio gli indici columnstore, per ottenere prestazioni migliori. Le funzionalità più recenti consentono di batch-train molti modelli di piccole dimensioni in parallelo in set di dati partizionato o assegnare un punteggio milioni di righe nel codice SQL nativo ottimizzato per l'attività di machine learning.
5. Per iniziare la di accuratezza Tramite le stored procedure, è possibile esporre facilmente le soluzioni predittive per le applicazioni esterne o di stack di Business Intelligence.

## <a name="related-products"></a>Prodotti correlati

Non si è certi che machine learning soluzione adatta alle proprie esigenze? Oltre a analitica incorporato in SQL Server 2016 e SQL Server 2017, Microsoft fornisce il computer seguente apprendimento piattaforme e servizi:

+ [Microsoft R Server e Server di Machine Learning](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)

  Un ambiente multi-piattaforma per lo sviluppo, distribuzione e gestione dei processi di machine learning
+ [Macchina virtuale per operazioni di data science](https://docs.microsoft.com/azure/machine-learning/machine-learning-data-science-virtual-machine-overview)

  Tutti gli strumenti che necessari per machine learning, preinstallato. Utilizzare server Jupyter notebook, Python o R.
  
  Provare il nuovo [edizione Windows 2016](http://aka.ms/dsvm/win2016), incluse le versioni GPU del Framework di formazione più diffusi, ad esempio CNTK mxNet, nonché il supporto per i contenitori di Windows.

+ [Servizi cognitivi Azure](https://azure.microsoft.com/services/cognitive-services/)

  Un'ampia gamma di servizi cloud per l'aggiunta AI e ML nelle applicazioni, incluso il linguaggio naturale l'indicizzazione del riconoscimento facciale, video, rilevamento emozioni, analitica di testo, computer più traduzioni e molto,
+ [Azure Machine Learning](https://azure.microsoft.com/services/machine-learning/)

  Un'interfaccia di trascinamento e rilascio basato su cloud per la progettazione di machine learning flussi di lavoro associate con la possibilità di automatizzare e integrare con le applicazioni tramite servizi web e PowerShell

## <a name="see-also"></a>Vedere anche

[Confrontare i prodotti Server di Machine Learning e Microsoft R](https://docs.microsoft.com/machine-learning-server/what-is-r-server-interoperability)
