---
title: Eventi estesi per il monitoraggio delle istruzioni di stima | Documenti Microsoft
titleSuffix: SQL Server
ms.custom: ''
ms.date: 03/01/2018
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: d517da44f989620003fef35d2e4721eead15d5d5
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2018
---
# <a name="extended-events-for-monitoring-predict-statements"></a>Eventi estesi per il monitoraggio delle istruzioni di stima

Questo articolo vengono descritti gli eventi estesi forniti in SQL Server che è possibile utilizzare per monitorare e analizzare i processi che utilizzano [PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) per eseguire l'assegnazione dei punteggi in tempo reale in SQL Server.

Punteggi in tempo reale generare punteggi da un modello di machine learning che è archiviato in SQL Server. La funzione di stima non richiede un runtime esterni, ad esempio R o Python, solo un modello che è stato creato utilizzando un formato binario specifico. Per ulteriori informazioni, vedere [assegnazione dei punteggi in tempo reale](https://docs.microsoft.com/sql/advanced-analytics/real-time-scoring).

## <a name="prerequisites"></a>Prerequisiti

Per informazioni generali relative a eventi estesi (talvolta denominati XEvent) e come tenere traccia degli eventi in una sessione, vedere i seguenti articoli:

+ [Concetti degli eventi estesi e l'architettura](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)
+ [Impostare l'acquisizione di eventi di SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/extended-events/quick-start-extended-events-in-sql-server)
+ [Gestire sessioni di eventi in Esplora oggetti](https://docs.microsoft.com/sql/relational-databases/extended-events/manage-event-sessions-in-the-object-explorer)

## <a name="table-of-extended-events"></a>Tabella degli eventi estesi

Eventi estesi seguenti sono disponibili in tutte le versioni di SQL Server che supportano il [T-SQL stimare](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql) istruzione, incluso SQL Server in Linux e il Database SQL di Azure. 

L'istruzione T-SQL stimare è stata introdotta in SQL Server 2017. 

|name |object_type|description| 
|----|----|----|
|predict_function_completed |evento  |Suddivisione del tempo di esecuzione Builtin|
|predict_model_cache_hit |evento|Si verifica quando un modello viene recuperato dalla cache del modello di funzione di stima. Usare questo evento con altri eventi predict_model_cache_ * per risolvere i problemi causati dalla cache dei modelli di funzione di stima.|
|predict_model_cache_insert |evento  |   Si verifica quando un modello di inserimento nella cache dei modelli di funzione di stima. Usare questo evento con altri eventi predict_model_cache_ * per risolvere i problemi causati dalla cache dei modelli di funzione di stima.    |
|predict_model_cache_miss   |evento|Si verifica quando un modello non viene trovato nella cache dei modelli di funzione di stima. Le occorrenze di frequente di questo evento può indicare che SQL Server è insufficiente. Usare questo evento con altri eventi predict_model_cache_ * per risolvere i problemi causati dalla cache dei modelli di funzione di stima.|
|predict_model_cache_remove |evento| Si verifica quando un modello viene rimosso dalla cache del modello per la funzione di stima. Usare questo evento con altri eventi predict_model_cache_ * per risolvere i problemi causati dalla cache dei modelli di funzione di stima.|

## <a name="query-for-related-events"></a>Query per gli eventi correlati

Per visualizzare un elenco di tutte le colonne restituite per questi eventi, eseguire la query seguente in SQL Server Management Studio:

```sql
SELECT * FROM sys.dm_xe_object_columns WHERE object_name LIKE `predict%'
```

## <a name="examples"></a>Esempi

Per acquisire informazioni sulle prestazioni di una sessione di punteggio usando stima:

1. Creare un nuovo oggetto esteso sessione eventi, utilizzando Management Studio o in un altro supportato [strumento](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events-tools).
2. Aggiungere gli eventi `predict_function_completed` e `predict_model_cache_hit` alla sessione.
3. Avviare la sessione eventi estesi.
4. Eseguire la query che utilizza la stima.

Nei risultati, esaminare queste colonne:

+ Il valore per `predict_function_completed` Mostra il tempo impiegata per il caricamento del modello e l'assegnazione dei punteggi query.
+ Il valore booleano per `predict_model_cache_hit` indica se la query utilizzato un modello memorizzato nella cache o meno. 

### <a name="native-scoring-model-cache"></a>Cache del modello punteggio nativo

Oltre agli eventi specifici da stimare, è possibile utilizzare le query seguenti per ottenere ulteriori informazioni sulla modello memorizzato nella cache e utilizzo di cache:

Visualizzare la cache del modello punteggio nativo:

```sql
SELECT *
FROM sys.dm_os_memory_clerks
WHERE type = 'CACHESTORE_NATIVESCORING';
```

Visualizzare gli oggetti nella cache dei modelli:

```sql
SELECT *
FROM sys.dm_os_memory_objects
WHERE TYPE = 'MEMOBJ_NATIVESCORING';
```

