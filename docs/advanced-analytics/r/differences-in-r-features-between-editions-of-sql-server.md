---
title: "SQL Server Machine Learning Services - disponibilità delle funzionalità tra edizioni | Documenti Microsoft"
ms.custom: 
ms.date: 03/07/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 16ca6c44b15c9fb7c1983d5a04175ebbade57895
ms.sourcegitcommit: 6b1618aa3b24bf6759b00a820e09c52c4996ca10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="feature-availability-across-editions-of-sql-server-machine-learning-services"></a>La disponibilità di funzionalità tra le edizioni di SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 Funzionalità di Machine learning sono disponibili in SQL Server 2016 e SQL Server 2017. In questo articolo sono elencate le edizioni che fornisce la funzionalità, vengono descritte le limitazioni si applicano in edizioni specifiche e vengono elencate le funzionalità disponibili solo in alcune edizioni.

 > [!NOTE]
 > In generale, Machine Learning (In-Database) di SQL Server non include il [rendere operativo il](https://docs.microsoft.com/machine-learning-server/what-is-operationalization) funzionalità incluse in un'installazione di R Server o Server di Machine Learning autonoma. Rendere operativo include distribuzione del servizio web e l'hosting e pertanto in competizione per le stesse risorse di altre operazioni di SQL Server.
 > 
 > Per questo motivo, si consiglia di installare SQL Server 2016 R Server (Standalone) o SQL Server 2017 Machine Learning Server (Standalone) in un diverso server fisico per supportare la distribuzione di modelli predittivi come servizio web. 

## <a name="sql-server-2017-machine-learning-services-in-database-and-standalone"></a>SQL Server 2017 Machine Learning Services (In-Database) e (autonomo)

L'edizione Developer Edition offre prestazioni equivalente a quella dell'edizione Enterprise. Utilizzo di Developer Edition non è supportato per gli ambienti di produzione.

|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------|----------|--------|---|------------------------------|-------|
| Interprete R & proprietari pacchetti | Sì | Sì | No | No | no | 
| Librerie client & interprete Python | Sì | Sì | No | No | no | 
| Suddivisione in blocchi di dati <br/>(grandi quantità di dati, oltre a ciò che rientra nella memoria di processo) | Sì | No | No | No | no |
| Elaborazione di scalabilità verticale <br/>(più di 2 processori) | Sì | No | No | No | no |
| Rendere operativo | Sì | No | No | No | no |
| [STIMARE](../../t-sql/queries/predict-transact-sql.md) (funzione) <br/>(esegue [punteggio native](../sql-native-scoring.md) su un modello con training preliminare, salvato in precedenza nel formato binario richiesto) | Sì | Sì | Sì | Sì | Sì |
| Compatibilità del Client di R | Sì | Sì | No | No | no | 
| Microsoft R Open | Sì | Sì | No | No | no | 
| Python anaconda 3.5 | Sì | Sì | No | No | no | 

## <a name="sql-server-2016-r-services-in-database-and-r-server-standalone"></a>R Server (Standalone) e SQL Server 2016 R Services (In-Database)

Disponibilità delle funzionalità corrisponde al 2017, meno il supporto di Python che non fa parte della versione 2016 prima.

## <a name="r-feature-availability-in-azure-sql-database"></a>Disponibilità delle funzionalità di R in Database SQL di Azure
  
Dopo una versione di prova iniziale è attualmente R Services **non** disponibili nel Database di SQL Azure, in attesa di ulteriore sviluppo. 

## <a name="performance-expectations-for-enterprise-edition"></a>Aspettative di prestazioni per Enterprise Edition

Prestazioni delle soluzioni di machine learning in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è previsto che in genere superano le implementazioni con R convenzionale assegnato lo stesso hardware. Che dipende dal fatto che in SQL Server, è possono eseguire soluzioni R usando risorse del server e talvolta distribuite a più processi mediante il **RevoScaleR** funzioni. 

Le prestazioni non sono stata valutata per le soluzioni di Python, come la funzionalità è ancora in fase di sviluppo, ma è previsto un alcuni dei vantaggi offerti da applicare.

Gli utenti possono prevedere anche visualizzare le differenze notevoli nelle prestazioni e scalabilità nella stessa soluzione di machine learning se eseguito in Visual Studio Enterprise Edition. Standard Edition. Motivi includono il supporto per parallel l'elaborazione, aumentare i thread disponibili per machine learning e streaming (o la suddivisione in blocchi), che consente le funzioni RevoScaleR gestire più dati possono adattarsi alla memoria. 

Tuttavia, può influire sulle prestazioni anche nello stesso hardware da molti fattori all'esterno del codice R o Python. Questi fattori sulle richieste di risorse del server, il tipo di piano di query che viene creato, le modifiche dello schema, la necessità di aggiornare le statistiche o creare un nuovo piano di query, la frammentazione e altro ancora. È possibile che una stored procedure contenente il codice R o Python potrebbero essere eseguiti in secondi sotto un carico di lavoro, ma richiedere minuti se sono presenti altri servizi in esecuzione.  È pertanto consigliabile monitorare più aspetti di prestazioni del server, tra cui la rete per contesti di calcolo remoto, durante la misurazione delle prestazioni di machine learning.

È inoltre consigliabile configurare [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) (disponibile nell'edizione Enterprise) per personalizzare la modalità che i processi di script esterni vengono ordinati in o gestiti in carichi di lavoro elevato sul server. È possibile definire le funzioni di classificazione per specificare l'origine del processo dello script esterno e stabilire le priorità di alcuni carichi di lavoro, limitare la quantità di memoria utilizzata dalle query SQL e controllare il numero di processi paralleli consente l'utilizzo del carico di lavoro.

## <a name="see-also"></a>Vedere anche

+ [Edizioni e componenti di SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [Edizioni e componenti di SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md)
+ [Suggerimenti per l'elaborazione dati di grandi dimensioni in R (Server di Machine Learning)](https://docs.microsoft.com/machine-learning-server/r/tutorial-large-data-tips)
