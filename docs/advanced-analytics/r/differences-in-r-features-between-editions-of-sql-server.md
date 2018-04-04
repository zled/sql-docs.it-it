---
title: SQL Server Machine Learning Services - disponibilità delle funzionalità tra edizioni | Documenti Microsoft
ms.custom: ''
ms.date: 03/17/2018
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: b64e836dc8969058e5012197e85fa78d40b87ac6
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="feature-availability-across-editions-of-sql-server-machine-learning-services"></a>La disponibilità di funzionalità tra le edizioni di SQL Server Machine Learning Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 Funzionalità di Machine learning sono disponibili in SQL Server 2016 e SQL Server 2017. In questo articolo sono elencate le edizioni che fornisce la funzionalità, vengono descritte le limitazioni si applicano in edizioni specifiche e vengono elencate le funzionalità disponibili solo in alcune edizioni.


## <a name="sql-server-2017-features"></a>Funzionalità di SQL Server 2017

Edizioni Enterprise e Developer hanno la stessa copertura di funzionalità in modo che è possibile compilare soluzioni per un'installazione Enterprise senza incorrere nel costo stesso. Sebbene le edizioni sono funzionalmente equivalenti, l'utilizzo dell'edizione Developer non è supportato per gli ambienti di produzione.

La differenza tra l'integrazione di base e avanzata è la scala. Integrazione avanzata è possibile utilizzare tutti i core disponibili per l'elaborazione parallela dei set di dati in qualsiasi dimensione adeguato per il computer. Integrazione di base è limitato a 2 core e set di dati rientra in memoria. 

Integrazione di base e avanzato si applica alle istanze (In-Database). Un server autonomo non è una funzione di istanza del motore di database e viene offerto come un'opzione di installazione solo nelle edizioni Enterprise e Developer.

|Funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Integrazione di R di base|Sì|Sì|Sì|Sì|no|   
|Integrazione di R avanzato|Sì|No|No|No|no| 
|Integrazione di Python di base|Sì|Sì|Sì|Sì|no|
|Integrazione di Python avanzata|Sì|No|No|No|no| 
|Machine Learning Server (Standalone)|Sì|No|No|No|no|   

 > [!NOTE]
 > Solo un server (Standalone) offre le [rendere operativo il](https://docs.microsoft.com/machine-learning-server/what-is-operationalization) funzionalità incluse in un Microsoft (non SQL-personalizzata) R Server o Server di Machine Learning installazione. Rendere operativo il include distribuzione del servizio web e funzionalità di hosting.
>
> Per un'installazione (In-Database), l'approccio equivalente per operatività soluzioni è sfruttando le funzionalità del motore di database, quando si converte il codice a una funzione che può eseguire in una stored procedure.


## <a name="sql-server-2016-r-features"></a>Funzionalità di SQL Server 2016 R

SQL Server 2016 include solo l'integrazione di R. In SQL Server 2016, integrazione di R di base e avanzato sono equivalenti a SQL Server 2017.

## <a name="r-feature-availability-in-azure-sql-database"></a>Disponibilità delle funzionalità di R in Database SQL di Azure
  
Dopo il rilascio di un test iniziale, R Services è stato rimosso dal Database di SQL Azure, in attesa di ulteriore sviluppo. 

## <a name="performance-expectations-for-enterprise-edition"></a>Aspettative di prestazioni per Enterprise Edition

Prestazioni delle soluzioni di machine learning in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è previsto che in genere superano le implementazioni con R convenzionale assegnato lo stesso hardware. Che dipende dal fatto che in SQL Server, è possono eseguire soluzioni R usando risorse del server e talvolta distribuite a più processi mediante il **RevoScaleR** funzioni. 

Gli utenti possono prevedere anche visualizzare le differenze notevoli nelle prestazioni e scalabilità nella stessa soluzione di machine learning se eseguito in Visual Studio Enterprise Edition. Standard Edition. Motivi includono il supporto per parallel l'elaborazione, aumentare i thread disponibili per machine learning e streaming (o la suddivisione in blocchi), che consente le funzioni RevoScaleR gestire più dati possono adattarsi alla memoria. 

Tuttavia, può influire sulle prestazioni anche nello stesso hardware da molti fattori all'esterno del codice R o Python. Questi fattori sulle richieste di risorse del server, il tipo di piano di query che viene creato, le modifiche dello schema, la necessità di aggiornare le statistiche o creare un nuovo piano di query, la frammentazione e altro ancora. È possibile che una stored procedure contenente il codice R o Python potrebbero essere eseguiti in secondi sotto un carico di lavoro, ma richiedere minuti se sono presenti altri servizi in esecuzione.  È pertanto consigliabile monitorare più aspetti di prestazioni del server, tra cui la rete per contesti di calcolo remoto, durante la misurazione delle prestazioni di machine learning.

È inoltre consigliabile configurare [Resource Governor](../../relational-databases/resource-governor/resource-governor.md) (disponibile nell'edizione Enterprise) per personalizzare la modalità che i processi di script esterni vengono ordinati in o gestiti in carichi di lavoro elevato sul server. È possibile definire le funzioni di classificazione per specificare l'origine del processo dello script esterno e stabilire le priorità di alcuni carichi di lavoro, limitare la quantità di memoria utilizzata dalle query SQL e controllare il numero di processi paralleli consente l'utilizzo del carico di lavoro.

## <a name="see-also"></a>Vedere anche

+ [Edizioni e componenti di SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)
+ [Edizioni e componenti di SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md)
+ [Suggerimenti per l'elaborazione dati di grandi dimensioni in R (Server di Machine Learning)](https://docs.microsoft.com/machine-learning-server/r/tutorial-large-data-tips)
