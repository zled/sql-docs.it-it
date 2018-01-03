---
title: Introduzione a SQL Server Machine Learning | Documenti Microsoft
ms.custom: SQL2016_New_Updated
ms.date: 12/07/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 5b28a663-effe-41f6-9bda-eda95f0c6943
caps.latest.revision: "34"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c114d320e71a93ffc6614ae6cfb1b535af2510e1
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="getting-started-with-sql-server-machine-learning"></a>Introduzione a SQL Server Machine Learning

Machine Learning Services in SQL Server è progettato per supportare le attività di analisi scientifica dei dati senza esporre i dati per i rischi di sicurezza o unnecesarily lo spostamento di dati.

+ In SQL Server 2016, è possibile lavorare con gli strumenti di R Preferiti, ma l'analisi a miliardi di record di scala ottimizzando le prestazioni. L'integrazione di apprendimento con SQL Server significa anche che è possibile inserire codice R nell'ambiente di produzione senza dover nuovamente codice.

+ SQL Server 2017 aggiunge il supporto per il codice Python, utilizzando lo stesso framework di estendibilità.

In questo argomento vengono descritti gli scenari chiavi per l'uso di R o Python nel database e fornisce le risorse che consentono di iniziare con soluzioni personalizzate.

Si applica a: R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services (In-Database)

> [!NOTE]
> SQL Server 2016 include il supporto solo per il linguaggio R. Supporto per linguaggio Python richiede SQL Server 2017 CTP 2.0.

## <a name="step-1-set-up-sql-server-machine-learning-services"></a>Passaggio 1. Impostare i servizi SQL Server Machine Learning

1. Eseguire il programma di installazione di SQL Server e installare almeno un'istanza del motore di database di SQL Server.
2. Aggiungere la funzionalità che supporta l'esecuzione di runtime esterni.
3. In SQL Server 2016, R viene aggiunto per impostazione predefinita. In SQL Server 2017, è necessario selezionare una lingua da aggiungere. È possibile selezionare R o Python o abilitare entrambi.
4. Al termine dell'installazione, eseguire alcuni passaggi aggiuntivi per consentire l'esecuzione dello script esterno e riavviare il server.

**Risorse**

+ [Configurare SQL Server con Machine Learning](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

> [!TIP]  
> È necessario creare un server per i processi R ma non è necessario SQL Server? Provare [Microsoft R Server](https://msdn.microsoft.com/library/mt674874.aspx).  

## <a name="step-2-develop-your-r-or-python-solutions"></a>Passaggio 2. Sviluppare il R o soluzioni di Python

Gli esperti di dati usano R o Python workstation i propri computer portatile o sviluppo, per esplorare i dati e di compilazione e ottimizzare i modelli predittivi fino a raggiungere un modello predittivo soddisfacente. 

Con Machine Learning Services in SQL Server, non è necessario modificare questo processo. Al termine dell'installazione, è possibile eseguire codice R o Python [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modalità locale o remota:

![rsql_keyscenario2](media/rsql-keyscenario2.png) 

+ **Usare l'IDE si preferisce**. I componenti client[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] offrono tutti gli strumenti necessari all'esperto di dati per le attività di sperimentazione e sviluppo. Gli strumenti includono il runtime di R e la libreria del kernel matematico di Intel, che migliorano le prestazioni delle operazioni standard di R, oltre a un set di pacchetti R avanzati che supportano l'esecuzione del codice R in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

+ **Lavorare in remoto o locale**. Come di consueto, gli esperti possono connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e aggiornare i dati nel client per l'analisi in locale. Una soluzione migliore consiste nell'usare le API **ScaleR** per trasferire i calcoli sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , evitando spostamenti costosi e non sicuri.

+ **Incorporare script R o Python in [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure**. Quando il codice è completamente ottimizzato, eseguirne il wrapping in una stored procedure per evitare lo spostamento dei dati non necessari e ottimizzare le operazioni di elaborazione dati.


**Risorse**

+ Installare [strumenti R per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation) o RStudio.  

## <a name="step-3-optimize"></a>Passaggio 3. Ottimizzazione

Quando il modello è pronto essere scalato in dati aziendali, l'esperto di dati spesso funzionerà con lo sviluppatore di amministratore di database o SQL per ottimizzare i processi, ad esempio:

+ Progettazione delle funzionalità
+ Inserimento di dati e la trasformazione dei dati
+ Assegnazione dei punteggi

Gli esperti di dati con R sono sempre state problemi di prestazioni e scalabilità, soprattutto quando si utilizzano i dataset di grandi dimensioni. Ciò avviene perché l'implementazione di common runtime è a thread singolo e può gestire solo i set di dati che rientrano nella memoria disponibile nel computer locale. Integrazione con servizi di SQl Server Machine Learning fornisce più funzionalità per ottenere prestazioni migliori, con ulteriori dati:

+ **RevoScaleR**.: pacchetto R questo contiene le implementazioni di alcune delle funzioni R più diffuse, riprogettate per garantire parallelismo e scalabilità. Il pacchetto include anche funzioni che incrementano scalabilità e prestazioni trasferendo i calcoli sul computer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dotato in genere di più memoria e potenza di calcolo.

+ **revoscalepy**. Questa libreria Python, nuova e disponibile solo in SQL Server 2017 CTP 2.0 implementa funzioni più diffuse in RevoScaleR, ad esempio contesti di calcolo remoti e numerosi algoritmi che supportano l'elaborazione distribuita.

+ Scegliere il linguaggio più adatto per l'attività.  R è ideale per i calcoli statistici difficili da implementare con SQL. Per le operazioni sui dati basata su set, sfruttare la potenza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ottenere prestazioni ottimali. Utilizzare il motore di database in memoria per i calcoli molto veloci su colonne.

**Risorse**

+ [Case study sulle prestazioni](../../advanced-analytics/r/performance-case-study-r-services.md)
+ [R e ottimizzazione dei dati](../../advanced-analytics/r/r-and-data-optimization-r-services.md)


## <a name="step-4-deploy-and-consume"></a>Passaggio 4. Distribuire e utilizzare

Quando lo script R o il modello è pronto per la produzione, uno sviluppatore di database può incorporare il codice o un modello in una stored procedure, in modo che il codice R o Python salvato può essere chiamato da un'applicazione. L'archiviazione e l'esecuzione di codice R da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenta numerosi vantaggi: è possibile usare l'interfaccia intuitiva di [!INCLUDE[tsql](../../includes/tsql-md.md)] e tutti i calcoli avvengono nel database evitando spostamenti di dati non necessari.

![rsql_keyscenario1](media/rsql-keyscenario1.png)

+ **Sicuro ed estendibile**. [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] usa una nuova architettura di estendibilità che protegge il motore di database e isola le sessioni di R. Consente inoltre di controllare gli utenti autorizzati a eseguire gli script R e di specificare quali database sono accessibili dal codice R. : è possibile controllare la quantità di risorse allocate al runtime di R, per evitare che calcoli di grande entità possano compromettere le prestazioni complessive del server.

+ **Pianificazione e controllo**. Se vengono eseguiti i processi di script esterni in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è possibile controllare e i dati di controllo utilizzato dagli esperti di dati. È inoltre possibile pianificare i processi e creare flussi di lavoro contenenti script R o Python esterni, esattamente come qualsiasi altro processo T-SQL o stored procedure, è consigliabile pianificare.

Per sfruttare i vantaggi delle funzionalità securty e gestione delle risorse in SQL Server, il processo di distribuzione potrebbe includere queste attività:

+ Conversione del codice R a una funzione che possono essere eseguiti in modo ottimale in una stored procedure
+ L'impostazione della sicurezza e il blocco di pacchetti utilizzati da un'attività specifica
+ Abilitazione di governance delle risorse

**Risorse**

+ [Governance delle risorse per R](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [Gestione dei pacchetti R per SQL Server](../../advanced-analytics/r/r-package-management-for-sql-server-r-services.md)

## <a name="quick-starts"></a>Avvio rapido

Leggere questa procedura dettagliata per comprendere il flusso di lavoro completo, di esplorazione dei dati per la creazione di un modello e la distribuzione in SQL Server.

+ [Procedura dettagliata end-to-end per l'analisi scientifica dei dati](../tutorials/walkthrough-data-science-end-to-end-walkthrough.md)

Informazioni su come utilizzare il pacchetto RevoScaleR per l'analisi di scalabili e a elevate prestazioni.

+ [Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)

In particolare per gli sviluppatori di dati, tutto il codice R fornite! Informazioni su come incorporare R nelle stored procedure SQL per creare o eseguire il training di modelli e ottenere stime da un modello archiviato.

+ [Analisi avanzata nel database per sviluppatori SQL](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Apprendere la sintassi per chiamare R da una stored procedure.

+ [Usare il codice R in Transact-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)

## <a name="solutions"></a>Soluzioni

Per ulteriori esempi, inclusi settore = modelli di soluzioni specifiche, vedere [esercitazioni di SQL Server Machine Learning](../tutorials/machine-learning-services-tutorials.md).
