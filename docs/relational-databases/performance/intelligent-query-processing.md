---
title: Elaborazione di query intelligenti nei database Microsoft SQL | Microsoft Docs
description: Funzionalità di elaborazione di query intelligenti e miglioramento delle prestazioni delle query in SQL Server e nel database SQL di Azure.
ms.custom: ''
ms.date: 07/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords: ''
ms.assetid: ''
author: joesackmsft
ms.author: josack
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 20c453617ccef36166ca3b9fae62ee0430959e51
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562955"
---
# <a name="intelligent-query-processing-in-sql-databases"></a>Elaborazione di query intelligenti nei database SQL
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-xx-asdb-xxxx-xxx-md.md)]

La famiglia di funzionalità di **elaborazione di query intelligenti** include funzionalità ad ampio spettro che migliorano le prestazioni di carichi di lavoro esistenti con un impegno minimo per l'implementazione.

![Funzionalità di elaborazione di query intelligenti](./media/1_IQPFeatureFamily.png)

## <a name="adaptive-query-processing"></a>Elaborazione di query adattive
La famiglia di funzionalità di elaborazione di query adattive include miglioramenti di elaborazione delle query che adattano le strategie di ottimizzazione alle condizioni di runtime del carico di lavoro dell'applicazione. Questi miglioramenti includono: join adattivi in modalità batch, feedback delle concessioni di memoria ed esecuzione interleaved per funzioni con valori di tabella a più istruzioni.

### <a name="batch-mode-adaptive-joins"></a>Join adattivi in modalità batch
Questa funzionalità consente al piano di passare in modo dinamico a una strategia di join più efficace durante l'esecuzione di un singolo piano memorizzato nella cache.

### <a name="row-and-batch-mode-memory-grant-feedback"></a>Disabilita il feedback delle concessioni di memoria in modalità riga e batch
Questa funzionalità ricalcola la memoria effettiva necessaria per una query e poi aggiorna il valore di concessione per il piano memorizzato nella cache, riducendo il numero eccessivo di concessioni che limita la concorrenza e correggendo il numero insufficiente di concessioni che causa costose distribuzioni su disco.

### <a name="interleaved-execution-for-multi-statement-table-valued-functions-mstvfs"></a>Esecuzione interleaved per funzioni con valori di tabella a più istruzioni
Con l'esecuzione interleaved, il conteggio effettivo delle righe viene usato per adottare decisioni più mirate relativamente a un piano di query downstream. 

Per altre informazioni, vedere [Elaborazione di query adattive nei database SQL](../../relational-databases/performance/adaptive-query-processing.md).

## <a name="table-variable-deferred-compilation"></a>Compilazione posticipata delle variabili di tabella
La compilazione posticipata delle variabili di tabella migliora la qualità del piano e le prestazioni generali per le query che fanno riferimento a variabili di tabella. Durante l'ottimizzazione e la compilazione iniziale, questa funzionalità propagherà le stime della cardinalità basate sui conteggi effettivi delle righe di variabili di tabella.  Queste informazioni accurate sui conteggi di righe verranno usate per l'ottimizzazione delle operazioni del piano downstream.

Con la compilazione posticipata delle variabili di tabella, la compilazione di un'istruzione che fa riferimento a una variabile di tabella viene posticipata fino alla prima esecuzione effettiva dell'istruzione. Questo comportamento di compilazione posticipata è identico a quello delle tabelle temporanee e con questo cambiamento viene usata la cardinalità effettiva invece dell'ipotesi originale basata su una sola riga. Per abilitare l'anteprima pubblica della compilazione posticipata delle variabili di tabella nel database SQL di Azure, abilitare il livello di compatibilità del database 150 per il database a cui si è connessi quando si esegue la query.

Per altre informazioni, vedere [Compilazione posticipata delle variabili di tabella](../../t-sql/data-types/table-transact-sql.md#table-variable-deferred-compilation ).

## <a name="approximate-query-processing"></a>Elaborazione delle query approssimativa
L'elaborazione delle query approssimative è una nuova famiglia di funzionalità progettata per fornire aggregazioni su set di dati di grandi dimensioni in cui la velocità di risposta è più importante della precisione assoluta.  Un esempio potrebbe essere il calcolo di COUNT(DISTINCT()) su 10 miliardi di righe, per la visualizzazione in un dashboard.  In questo caso, la precisione assoluta non è importante, ma la velocità di risposta è fondamentale. La nuova funzione di aggregazione APPROX_COUNT_DISTINCT restituisce il numero approssimativo di valori univoci non Null in un gruppo.

Per altre informazioni, vedere [APPROX_COUNT_DISTINCT (Transact-SQL)](../../t-sql/functions/approx-count-distinct-transact-sql.md).

## <a name="see-also"></a>Vedere anche
[Centro prestazioni per il motore di database di SQL Server e il database SQL di Azure](../../relational-databases/performance/performance-center-for-sql-server-database-engine-and-azure-sql-database.md)     
[Guida sull'architettura di elaborazione delle query](../../relational-databases/query-processing-architecture-guide.md)    
[Guida di riferimento a operatori Showplan logici e fisici](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
[Join](../../relational-databases/performance/joins.md)    
[Demonstrating Adaptive Query Processing](https://github.com/joesackmsft/Conferences/blob/master/Data_AMP_Detroit_2017/Demos/AQP_Demo_ReadMe.md) (Dimostrazione dell'elaborazione di query adattive)        
