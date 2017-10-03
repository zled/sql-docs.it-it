---
title: Uso di R in Database SQL di Azure | Documenti Microsoft
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 1
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: e3c781449a8f7a1b236508cd21b8c00ff175774f
ms.openlocfilehash: 619921bbf00801fd5930a1c1b110e69a9fd05a81
ms.contentlocale: it-it
ms.lasthandoff: 09/30/2017

---
# <a name="using-r-in-azure-sql-database"></a>Uso di R in Database SQL di Azure

A partire da ottobre 2017, Database SQL di Azure supporta l'esecuzione di R codice nel database utilizzando le stored procedure, simile a R Services in SQL Server 2016.

In questo articolo viene fornita una panoramica della funzionalità e vengono descritte le limitazioni note.

> [!NOTE]
> Questa versione è una versione di anteprima iniziale ed è destinata solo l'esplorazione e di test. Una versione di produzione verrà rilasciata in 2018 qualche minuto. La data di rilascio esatto e la build si baserà commenti degli utenti. Pertanto, è consigliabile provare la funzionalità e far conoscere le funzionalità che sono importanti. 
> 
> Per informazioni sulla pianificazione della versione, vedere il [blog di SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/) o [blog di Microsoft R Server](https://blogs.msdn.microsoft.com/rserver/).

## <a name="features"></a>Funzionalità

La versione di anteprima offre le funzionalità seguenti:

+ Chiamare R tramite stored procedure per facilitarne la distribuzione di soluzioni di apprendimento automatico
+ Ottenere punteggi dal modello utilizzando qualsiasi applicazione in grado di connettersi al database cloud
+ Supporta il punteggio nativa utilizzando la funzione di stima, per il punteggio rapido senza l'utilizzo del runtime di R

Per informazioni sulle restrizioni specifiche della versione di anteprima, vedere [limitazioni e problemi noti](#bkmk_restrictions).

### <a name="components"></a>Components

L'architettura complessiva è simile a quella di SQL Server macchina R Services.

**Sicurezza**

+ Il Launchpad attendibile di SQL Server gestisce l'esecuzione dei processi R e controlla la durata dei processi. 

**Pacchetti R**

+ La versione di anteprima include Microsoft R Open 3.3.3 e Microsoft R Server versioni 9.2. Il [pacchetto RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler) è preinstallato.

+ Alcuni pacchetti R sono stati rimossi o modificati per ridurre il footprint nell'ambiente Azure. Ad esempio, **mrsdeploy** non è incluso nel Database SQL di Azure.

**Prestazioni**

+ Supporta set di training e assegnazione dei punteggi da un modello in cui i dati possono essere inseriti in memoria.  La quantità di memoria disponibile dipende dall'edizione del database. 
+ Parallelismo semplice viene supportato usando il @parallel = 1 argomento, nonché il flusso per l'esecuzione di script R 
+ Nell'anteprima, limitata a un singolo script R eseguiti contemporaneamente per ogni database.

**Lingue**

Guida di orientamento per versioni future include il supporto per pacchetti aggiuntivi e Python.

## <a name="restrictions"></a>Restrizioni

In questa sezione sono elencate alcune limitazioni aggiuntive che si applicano alla versione di anteprima.

### <a name="upgrading-r-components-and-adding-packages-not-supported"></a>L'aggiornamento dei componenti di R e aggiunta di pacchetti non è supportati

Database SQL di Azure è un servizio gestito e i clienti non possono gestire gli aggiornamenti per i componenti di R. Per la versione di anteprima, usare i pacchetti installati disponibili.

Gli aggiornamenti a R e altri machine learning componenti verranno rilasciati appena diventano disponibili.

### <a name="availability"></a>Disponibilità

La possibilità di eseguire R e altri machine learning script nel Database di SQL Azure è una funzionalità di anteprima nella occidentale Stati Uniti centro area solo. Espansione in altre aree, ad esempio Europa occidentale, è previste per le versioni successive.

L'esecuzione di R in Database SQL di Azure richiede l'archiviazione e memoria sufficienti. Attualmente sono supportati i seguenti livelli di servizio di database e i livelli di prestazioni:

+ Livello di servizio Premium: P1, P2, P4, P6, P11, P15 
+ Livello di servizio RS Premium: PRS1, PRS2, PRS4, PRS6 
+ Pool elastico Premium: Edtu 125 o versione successiva 
+ Del Pool elastico RS Premium: numero di Edtu 125 o versione successiva 

### <a name="resource-management"></a>Gestione delle risorse

Questa versione non supporta la possibilità di personalizzare l'installazione di R, o per monitorare l'utilizzo di script R.

Ad esempio, è possibile abilitare l'esecuzione di script R solo su database specifici.

Sys.dm db_resource_stats DMV, utilizzato per monitorare l'utilizzo della CPU e memoria di script R, non è disponibile nella versione di anteprima.

### <a name="other-limitations"></a>Altre limitazioni

Non è supportata la seguente funzionalità: 

+ Il pacchetto MicrosoftML non è disponibile.
+ Funzionalità di gestione di pacchetti, ad esempio creare libreria esterna non sono supportate.
+ È possibile utilizzare il database SQL di Azure come un contesto di calcolo remoto durante l'esecuzione di script da un client di R. Tramite il sp_execute_external_script stored procedure, è necessario eseguire gli script R. Gli script chiamati la stored procedure non è possibile utilizzare altri contesti di calcolo.
+ È possibile eseguire le chiamate alle funzioni rx che richiedono l'esecuzione parallela.
+ Le connessioni loopback dallo script R per SQL Server non sono supportate. In altre parole, è possibile inviare chiamate esterne dallo script R da un'altra origine dati ODBC.

## <a name="get-started"></a>Introduzione

Questo annuncio dal team di sviluppo di SQL Server include i campioni breve che è possibile eseguire nei database SQL di Azure per provare la compilazione di modelli R e la generazione delle stime.

+ [Formazione e i modelli di punteggio in Database SQL di Azure](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2017/09/25/announcing-preview-of-machine-learning-services-with-r-support-in-azure-sql-database/)

