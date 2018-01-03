---
title: Analitica R nel database per gli sviluppatori SQL (esercitazione) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: c18cb249-2146-41b7-8821-3a20c5d7a690
caps.latest.revision: "15"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e3767912b2b2cd7390b1329ff1c584324e8bd673
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="in-database-r-analytics-for-sql-developers-tutorial"></a>Analitica R nel database per gli sviluppatori SQL (esercitazione)

L'obiettivo di questa esercitazione è fornire ai programmatori SQL con la creazione di un di machine learning soluzioni in SQL Server. In questa esercitazione verrà illustrato come incorporare R in un'applicazione o di una soluzione di Business Intelligence eseguendo il wrapping di codice R nelle stored procedure.

> [!NOTE]
> 
> Nella stessa soluzione è disponibile in Python. SQL Server 2017 è obbligatorio. Vedere [analitica nel database per gli sviluppatori di Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Panoramica

Il processo di creazione di una soluzione end-to-end normalmente consiste in attività di acquisizione e pulizia dei dati, esplorazione dei dati e progettazione di funzionalità, training e ottimizzazione del modello e infine distribuzione del modello nell'ambiente di produzione. Sviluppo e test del codice effettivo viene più eseguita utilizzando un ambiente di sviluppo dedicato. Per R, che potrebbe indicare RStudio o [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Dopo la creazione della soluzione, tuttavia è possibile distribuirla facilmente a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando le stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)] nell'ambiente familiare di [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

In questa esercitazione si presuppone che è stato assegnato tutto il codice R necessario per la soluzione e lo stato attivo sulla compilazione e distribuzione della soluzione Usa SQL Server.

- [Lezione 1: Scaricare i dati di esempio](../tutorials/sqldev-download-the-sample-data.md)

    Scaricare il set di dati di esempio e i file di script SQL di esempio in un computer locale.

- [Lezione 2: Importare dati in SQL Server tramite PowerShell](../r/sqldev-import-data-to-sql-server-using-powershell.md)

    Eseguire uno script di PowerShell che crea un database e una tabella nell'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e carica i dati di esempio nella tabella.

- [Lezione 3: Esplorare e visualizzare i dati](../tutorials/sqldev-explore-and-visualize-the-data.md)

    Eseguire l'esplorazione e la visualizzazione di base dei dati, chiamando pacchetti e funzioni R dalle stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)] .

- [Lezione 4: Creare funzionalità di dati con T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md)

    Creare nuove funzionalità di dati usando funzioni personalizzate di SQL.
  
-   [Lezione 5: Eseguire il training e salvare un modello R con T-SQL](../r/sqldev-train-and-save-a-model-using-t-sql.md)

    Compilare un modello di machine learning usando R nelle stored procedure. Salvare il modello a una tabella di SQL Server.
  
-   [Lezione 6: Rendere operativo il modello](../tutorials/sqldev-operationalize-the-model.md)

    Dopo aver salvato il modello per il database, chiamare il modello per la stima da [!INCLUDE[tsql](../../includes/tsql-md.md)] usando le stored procedure.

### <a name="scenario"></a>Scenario

Questa esercitazione viene utilizzato un noto pubblica set di dati in base a trip nei taxi New York city. Per eseguire il codice di esempio più velocemente, è stato creato un campione rappresentativo di % 1 dei dati. Utilizzare questi dati per compilare un modello di classificazione binaria che consente di stimare se un particolare trip è probabile che ottenere un suggerimento o non, in base alle colonne, ad esempio l'ora del giorno, distanza e posizione ritiro.

### <a name="requirements"></a>Requisiti

In questa esercitazione è destinata agli utenti che hanno già familiarità con operazioni fondamentali sui database, ad esempio la creazione di tabelle e database, l'importazione di dati in tabelle e la creazione di query SQL. È disponibile tutto il codice R, quindi non è richiesto un ambiente di sviluppo di R. Un programmatore SQL deve essere in grado di completare l'esempio utilizzando [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ed eseguendo gli script di PowerShell specificati.

Tuttavia, prima di iniziare l'esercitazione, è necessario completare le operazioni di preparazione:

- Connettersi a un'istanza di SQL Server 2016 con R Services o SQL Server 2017 con servizi di Machine Learning e R abilitato.
- L'account di accesso utilizzato per questa esercitazione è necessario disporre delle autorizzazioni per creare database e altri oggetti, per caricare i dati, selezionano i dati, eseguono le stored procedure.

> [!NOTE]
> È consigliabile effettuare **non** utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per scrivere o testare il codice R. Se il codice che viene incorporato in una stored procedure è presenti eventuali problemi, le informazioni che viene restituite dalla stored procedure sono in genere sufficienti per individuare la causa dell'errore.
> 
> Per il debug, si consiglia di usare uno strumento come [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], o RStudio. Gli script R contenuti in questa esercitazione sono già stati sviluppati e sottoposti a debug usando gli strumenti tradizionali di R.

## <a name="next-lesson"></a>Lezione successiva

[Lezione 1: Scaricare i dati di esempio](../tutorials/sqldev-download-the-sample-data.md)
