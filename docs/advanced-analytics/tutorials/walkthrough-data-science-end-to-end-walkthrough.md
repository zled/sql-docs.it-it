---
title: Procedura dettagliata di analisi scientifica dei dati end-to-end per R e SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs: R
ms.assetid: edd76ae9-4125-45a8-bf42-47a85b9d9a32
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 2fc213534da32bf529acdb85fd5b0288bf686068
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="end-to-end-data-science-walkthrough-for-r-and-sql-server"></a>Procedura dettagliata di analisi scientifica dei dati end-to-end per R e SQL Server

In questa procedura dettagliata, si sviluppa una soluzione end-to-end per la modellazione predittiva in base a Microsoft R con SQL Server 2016 o SQL Server 2017.

Questa procedura dettagliata è basata su un set di dati pubblico molto diffuso, il set di dati dei taxi di New York City. Utilizzare una combinazione di codice R, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati e funzioni SQL personalizzate per compilare un modello di classificazione che indica la probabilità che il driver è possibile che venga visualizzato un suggerimento in viaggio taxi particolare. È inoltre distribuire il modello R a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e utilizzare i dati del server per generare punteggi in base al modello.

In questo esempio può essere esteso a tutti i tipi di problemi reali, ad esempio stimare le risposte del cliente per le campagne di vendita o stima di spesa o presenza di eventi. Poiché il modello può essere richiamato da una stored procedure, è possibile incorporarlo facilmente in un'applicazione.

Poiché la procedura dettagliata è progettata per gli sviluppatori R per introdurre [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R viene utilizzato laddove possibile. Tuttavia, ciò non significa che R sia necessariamente lo strumento migliore per ogni attività. In molti casi, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] potrebbe offrire prestazioni migliori, in particolare in attività quali l'aggregazione dei dati e la progettazione delle funzionalità.  Tali attività possono trarre vantaggio dalle nuove funzionalità di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], ad esempio gli indici columnstore con ottimizzazione per la memoria. Si tenta di evidenziare le ottimizzazioni possibili lungo il percorso.

> [!NOTE]
> La procedura dettagliata è stata originariamente sviluppata e testata per SQL Server 2016. Tuttavia, le schermate e le procedure sono state aggiornate per utilizzare la versione più recente di SQL Server Management Studio, che funziona con SQL Server 2017.

## <a name="overview"></a>Panoramica

Stimati periodi non includono l'installazione. Per ulteriori informazioni, vedere [prerequisiti per la procedura dettagliata](../tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md).

|Elenco di argomenti|Tempo stimato|
|-|------------------------------|
|[Preparare i dati di questa procedura dettagliata di R](../tutorials/walkthrough-prepare-the-data.md) <br /><br />Ottenere i dati usati per la compilazione di un modello. Scaricare un set di dati pubblico e caricarlo in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|30 minuti|
|[Esplorare i dati usando R](../tutorials/walkthrough-view-and-explore-the-data.md) <br /><br />Comprensione dei dati utilizzando i riepiloghi e gli strumenti di SQL.|10 minuti|
|[Riepilogare i dati usando R](../tutorials/walkthrough-view-and-summarize-data-using-r.md) <br /><br />Usare R per esplorare i dati e generare riepiloghi.|10 minuti|
|[Creare grafici usando R in SQL Server](../tutorials/walkthrough-create-graphs-and-plots-using-r.md) <br /><br />Creare grafici in contesti di calcolo locali e remoti per la combinazione di R e SQL.|10 minuti|
|[Creare le funzionalità di dati con R e T-SQL)](../tutorials/walkthrough-create-data-features.md) <br /><br />Eseguire la progettazione di funzionalità usando funzioni personalizzate in R e [!INCLUDE[tsql](../../includes/tsql-md.md)]. Confrontare le prestazioni di R e T-SQL per le attività di creazione di funzionalità. |10 minuti|
|[Compilare un modello R e salvarlo in SQL Server](../tutorials/walkthrough-build-and-save-the-model.md) <br /><br />Eseguire il training di un modello predittivo e ottimizzarlo. Valutare le prestazioni del modello. Questa procedura dettagliata crea un modello di classificazione. Tracciare l'accuratezza del modello usando R.|15 minuti|
|[Distribuire il modello R con SQL Server](../tutorials/walkthrough-deploy-and-use-the-model.md) <br /><br />Distribuire il modello nell'ambiente di produzione salvandolo in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Chiamare il modello da una stored procedure per generare stime.|10 minuti|

### <a name="intended-audience"></a>Destinatari

Questa procedura dettagliata è destinata agli sviluppatori di R o SQL. Offre un'introduzione su come integrare R nei flussi di lavoro aziendali usando [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  È necessario conoscere le operazioni di database, ad esempio la creazione di tabelle e database, l'importazione di dati e l'esecuzione di query.

+ Tutti gli script SQL e R sono inclusi.
+ Si potrebbe essere necessario modificare le stringhe di script, per l'esecuzione nell'ambiente in uso. È possibile farlo con qualsiasi editor di codice, ad esempio [codice di Visual Studio](https://code.visualstudio.com/Download).

### <a name="prerequisites"></a>Prerequisiti

+ È necessario avere accesso a un'istanza di SQL Server 2016, o una versione di valutazione di SQL Server 2017.
+ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] deve essere installato in almeno un'istanza del computer SQL Server.
+ Se si desidera eseguire i comandi di R da un computer remoto, ad esempio un computer portatile o un altro computer in rete, è necessario installare le librerie Microsoft R Open. È possibile installare il Client R Microsoft o Microsoft R Server. Il computer remoto deve essere in grado di connettersi al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.
+ Se è necessario includere client e server nello stesso computer, assicurarsi di installare un set separato di librerie di Microsoft R da utilizzare per l'invio di script R da un client "remoto". Non utilizzare le librerie di R che vengono installate per l'utilizzo dall'istanza di SQL Server per questo scopo.

Per informazioni dettagliate su come configurare questi server e di ambienti client, vedere [prerequisiti per la procedura dettagliata di analisi scientifica dei dati a R e SQL Server](../tutorials/walkthrough-prerequisites-for-data-science-walkthroughs.md).

## <a name="next-lesson"></a>Lezione successiva

[Preparare i dati di questa procedura dettagliata di R](../tutorials/walkthrough-prepare-the-data.md)
