---
title: Usare i widget di informazioni per monitorare i server e database in Studio operazioni SQL (anteprima) | Documenti Microsoft
description: Informazioni sui widget di informazioni dettagliate in Studio operazioni SQL (anteprima).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d810e0b5ed89b93ac3d56a12758285fbd297092b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="manage-servers-and-databases-with-insight-widgets-in-includename-sosincludesname-sos-shortmd"></a>Gestire server e i database con i widget di informazioni in[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Widget Insight eseguire le query Transact-SQL (T-SQL) consentono di monitorare i server e database e trasformarli in visualizzazioni dettagliate. 

Informazioni dettagliate sono personalizzabili grafici e aggiunti al server e i dashboard di monitoraggio del database. Visualizza informazioni dettagliate in generale del server e database, quindi esaminare ulteriori dettagli, quindi avviare azioni di gestione che definiscono. 

È possibile compilare straordinario server e database di gestione dashboard simile all'esempio seguente:

![dashboard del database](media/insight-widgets/database-dashboard.png)


Per passare e iniziare a creare tipi diversi di widget informazioni dettagliate, vedere le esercitazioni seguenti:

- [Compilare un widget di informazioni personalizzate](tutorial-build-custom-insight-sql-server.md)
- *Abilitare i widget predefiniti insight*
   - [Abilita informazioni di monitoraggio delle prestazioni](tutorial-qds-sql-server.md)
   - [Abilitare le informazioni sull'utilizzo dello spazio di tabella](tutorial-table-space-sql-server.md)


## <a name="sql-queries"></a>Query SQL 

[!INCLUDE[name-sos](../includes/name-sos-short.md)]tenta di evitare di introdurre ancora un altro utente di lingua o elevati in termini di interfaccia in modo che si tenta di utilizzare T-SQL per quanto possibile con la configurazione minima di JSON. Configurazione widget insight con T-SQL sfrutta l'innumerevoli numero di origini esistenti di query T-SQL utili che possono essere attivate nel widget dettagliati.

Widget di informazioni dettagliate sono costituiti da uno o due query T-SQL:
* *Query sui widget Insight* è obbligatorio ed è la query che restituisce i dati visualizzati all'interno del widget.
* *Query di analisi dei dettagli* è necessaria solo se si sta creando una pagina di dettagli informazioni dettagliate.

Una query di widget insight definisce un set di dati che esegue il rendering di un numero, un grafico o un grafico. Query di analisi dei dettagli viene utilizzato per elencare le informazioni di dettaglio informazioni rilevanti in un formato tabulare nel riquadro dei dettagli informazioni dettagliate. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)]esegue query widget insight e il set di risultati della query viene eseguito il mapping a set di dati del grafico, quindi ne esegue il rendering. Quando gli utenti aprono i dettagli di un'informazione, esegue la query di dettagli informazioni dettagliate e stampa il risultato in una visualizzazione griglia nella finestra di dialogo.

L'idea di base consiste nello scrivere una query T-SQL in modo pertanto può essere utilizzato come un set di dati di un conteggio, grafico e widget grafico. 

## <a name="summary"></a>Riepilogo

La query T-SQL e il set di risultati determinano il comportamento di widget informazioni dettagliate. Scrittura di una query per un tipo di grafico o un tipo di grafico a destra per query esistenti di mapping è la considerazione chiave per compilare un widget insight effettivo.



## <a name="additional-resources"></a>Risorse aggiuntive
- [Editor di query](tutorial-sql-editor.md)

