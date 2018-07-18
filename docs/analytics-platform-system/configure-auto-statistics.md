---
title: Automatico delle statistiche (Analitica Platform System)
description: Descrive automatico delle statistiche funzionalità introdotto in Analitica piattaforma sistema AU7.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 1c0f4623adad35ab874330b42aa54f6e1b91d961
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
---
# <a name="configure-auto-statistics"></a>Configurare automaticamente le statistiche

Informazioni su come configurare Parallel Data Warehouse per l'utilizzo automatico statistiche per la creazione e aggiornamento automatico delle statistiche.  Utilizzare questa funzionalità per migliorare i piani di query e pertanto migliorare le prestazioni delle query.

**Si applica a:** APS (a partire AU7)

## <a name="what-are-statistics"></a>Quali sono le statistiche?
Le statistiche per l'ottimizzazione delle query sono oggetti contenenti informazioni statistiche sulla distribuzione dei valori in una o più colonne di una tabella. In query Optimizer queste statistiche per stimare la cardinalità o il risultato di numero di righe nella query. Queste stime della cardinalità consentono a query optimizer creare un piano di query di alta qualità. Ad esempio, nei punti di accesso, nella MPP query optimizer viene utilizzata la stima relativa alla cardinalità per scegliere casuale o la replica il meno elevato tra due tabelle utilizzate in una clausola join e in questo modo le prestazioni delle query.  Per altre informazioni, vedere [statistiche](../relational-databases/statistics/statistics.md) e [DBCC SHOW_STATISTICS](../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)

## <a name="what-are-auto-statistics"></a>Quali sono le statistiche di auto?
Le statistiche automatiche sono statistiche che query optimizer vengono create e aggiornate automaticamente per migliorare il piano di query. Le statistiche possono diventare non aggiornate dopo il caricamento, inseriscono, aggiornano ed Elimina le operazioni. Prive di statistiche automatiche, è necessario eseguire un'analisi personalizzata per comprendere le colonne necessarie statistiche e quando le statistiche dovranno essere aggiornati.

Statistiche automatico includono le seguenti tre impostazioni: 

### <a name="autocreatestatistics"></a>AUTO_CREATE_STATISTICS
Quando il creazione automatica opzione delle statistiche, AUTO_CREATE_STATISTICS, è impostata su ON, Query Optimizer Crea statistiche per colonne singole nel predicato della query, se necessario, per migliorare le stime della cardinalità per il piano di query. Queste statistiche di colonna singola vengono create in colonne che ancora non dispongono di un istogramma in un oggetto statistiche esistente.

### <a name="autoupdatestatistics"></a>AUTO_UPDATE_STATISTICS 
Quando l'opzione per l'aggiornamento automatico delle statistiche, AUTO_UPDATE_STATISTICS, è impostata su ON, Query Optimizer determina se le statistiche potrebbero non essere aggiornate, quindi ne esegue l'aggiornamento qualora vengano utilizzate tramite una query. Le statistiche diventare obsolete in seguito le operazioni inseriscono, update, delete o merge modificano la distribuzione dei dati nella tabella o vista indicizzata. Query Optimizer determina che le statistiche potrebbero non essere aggiornate contando il numero di modifiche apportate ai dati dopo l'ultimo aggiornamento delle statistiche e confrontando il numero di modifiche con una soglia basata sul numero di righe nella tabella o nella vista indicizzata.

### <a name="autoupdatestatisticsasync"></a>AUTO_UPDATE_STATISTICS_ASYNC
L'opzione relativa all'aggiornamento asincrono delle statistiche, AUTO_UPDATE_STATISTICS_ASYNC, determina se Query Optimizer usa gli aggiornamenti sincroni o asincroni delle statistiche. Per i punti di accesso, l'opzione relativa all'aggiornamento asincrono delle statistiche è impostata su ON per impostazione predefinita e Query Optimizer Aggiorna le statistiche in modo asincrono. L'opzione AUTO_UPDATE_STATISTICS_ASYNC si applica a oggetti statistiche creati per indici, colonne singole nei predicati di query e statistiche create con l'istruzione CREATE STATISTICS.

## <a name="configuration-settings-for-system-administrators"></a>Impostazioni di configurazione per gli amministratori di sistema
Dopo l'aggiornamento a AU7 APS, statistiche automatico sono abilitata per impostazione predefinita. L'amministratore di sistema può abilitare o disabilitare automatica statistiche con il [opzione della funzionalità](appliance-feature-switch.md) opzione in Gestione configurazione dello strumento.  Una volta abilitato, gli utenti possono modificare le impostazioni di statistiche per ogni database.
La modifica dei valori di parametro di funzione richiede un riavvio del servizio su punti di accesso.

## <a name="change-auto-statistics-settings-on-a-database"></a>Modificare le impostazioni di statistiche automatica in un database
Quando le statistiche automatico sono abilitata dall'amministratore di sistema, è possibile utilizzare [ALTER DATABASE (Parallel Data Warehouse)](/sql/t-sql/statements/alter-database-parallel-data-warehouse) per modificare le impostazioni di statistiche in un database. Se l'opzione della funzionalità statistiche automatico è abilitato dall'amministratore di sistema, i nuovi database creati dopo l'aggiornamento a AU7 avrà statistiche automatico abilitate. Tutti i database esistenti prima dell'aggiornamento a AU7 presentano statistiche automatico disabilitate. L'esempio seguente Abilita le statistiche automatiche per myPDW il database esistente.

```sql
ALTER DATABASE myPDW SET AUTO_CREATE_STATISTICS ON
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS ON 
ALTER DATABASE myPDW SET AUTO_UPDATE_STATISTICS_ASYNC ON
```
 
Opzione AUTO_UPDATE STATISTICS_ASYNC funziona solo se AUTO_UPDATE_STATISTICS è impostata su ON.  Pertanto, le statistiche non vengono aggiornate quando AUTO_UPDATE_STATISTICS è impostata su OFF e AUTO_UPDATE_STATISTICS_ASYNC è impostata su ON. 

### <a name="error-messages"></a>Messaggi di errore
Si potrebbe ricevere il messaggio di errore "questa opzione non è supportata in PDW".  Questo errore si verifica quando l'amministratore di sistema non è abilitato le statistiche automatiche, e si tenta di impostare uno qualsiasi dei automatica opzioni relative alle statistiche in ALTER DATABASE. 

### <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni
Statistiche automatico non funziona nelle tabelle esterne. 

### <a name="check-the-current-values"></a>Controllare i valori correnti
La query seguente restituisce i valori correnti delle impostazioni delle statistiche automatiche per tutti i database.

```sql
SELECT NAME
    , IS_AUTO_CREATE_STATS_ON 
    , IS_AUTO_UPDATE_STATS_ON
    , IS_AUTO_UPDATE_STATS_ASYNC_ON
FROM
    sys.databases;
```

Valore restituito pari a 1 indica l'impostazione è su e 0 indica che l'impostazione è disabilitata. 

## <a name="next-steps"></a>Passaggi successivi
Per modalità di esecuzione di query, vedere la sezione [monitoraggio delle query attive](monitoring-active-queries.md)
