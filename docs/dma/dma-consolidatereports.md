---
title: Consolidare le relazioni di valutazione (SQL Server Data Migration Assistant) | Documenti Microsoft
ms.custom: ''
ms.date: 04/16/2018
ms.prod: sql
ms.prod_service: dma
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-dma
ms.tgt_pltfrm: ''
ms.topic: article
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 30399ddacff6c84ea1f5d914f87b11dac02167b4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="consolidate-assessment-reports-data-migration-assistant"></a>Consolidare le relazioni di valutazione (dati della migrazione guidata)

È possibile utilizzare la riga di comando per eseguire le valutazioni relative alla migrazione in modalità automatica, a partire dalla Data Migration Assistant v 2.1. Questa funzionalità consente di eseguire valutazioni su larga scala. I risultati della valutazione sotto forma di un file JSON o CSV.

È possibile valutare più database in una sola istanza di utilità della riga di dati Migration Assistant ed esportare tutti i risultati delle valutazioni in un unico file JSON. In alternativa, è possibile valutare un database in esecuzione e in un secondo momento consolidare i risultati da questi più file JSON in un database SQL.

Per informazioni sulla modalità di esecuzione Data Migration Assistant dalla riga di comando, vedere [eseguire Data Migration Assistant dalla riga di comando](../dma/dma-commandline.md). 


## <a name="import-assessment-results-into-a-sql-server-database"></a>Importare i risultati della valutazione in un database di SQL Server

Usare lo script di PowerShell disponibile in questa [repository Github](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant) per importare i risultati della valutazione dal file JSON in un database di SQL Server.

> [!NOTE]
> PowerShell v5 o versione successiva è obbligatorio.

Quando si esegue lo script, è necessario fornire le informazioni seguenti: 

- **serverName**: nome dell'istanza di SQL Server che si desidera importare la valutazione risultati dal file JSON.

- **databaseName**: il nome del database che i risultati vengono importati per.

- **jsonDirectory**: la cartella che salvati i risultati della valutazione, in uno o più file JSON.

- **processTo**: SQLServer

Aggiungere i valori precedenti nella sezione "Esecuzione delle funzioni", come indicato di seguito.

```
dmaProcessor -serverName localhost \`\
-databaseName DMAReporting \`\
-jsonDirectory "C:\\temp\\DMACmd\\output\\" \`\
-processTo SQLServer
```

Lo script di PowerShell crea gli oggetti seguenti nell'istanza di SQL che è stato specificato, se gli oggetti non esistono già:

- **Database** : il nome specificato nei parametri di PowerShell

  - Archivio principale

- **Tabella** – attività

  - Dati per i report

- **Tabella** -BreakingChangeWeighting

  - Tabella di riferimento per tutte le modifiche di rilievo. È possibile definire i valori di ponderazione per poter influire sulla classificazione aggiornamento completato percentuale (%) più accurata.

- **Visualizzazione** – UpgradeSuccessRanking\_OnPrem

  - Consente di visualizzare la visualizzazione di un fattore di successo per ogni database per essere migrati in locale.

- **Visualizzazione** – UpgradeSuccessRanking\_Azure

  - Consente di visualizzare la visualizzazione di un fattore di successo per ogni database per essere migrati in locale.

- **Stored Procedure** – JSONResults\_Insert

  - Utilizzato per importare dati da un file JSON in SQL Server.

- **Stored Procedure** – AzureFeatureParityResults\_Insert

  - Utilizzato per importare i risultati di parità di funzionalità di Azure da un file JSON in SQL Server.

- **Tipo di tabella** – JSONResults

  - Utilizzato per archiviare i risultati JSON per le valutazioni di on-premise e passare il JSONResults\_inserire stored procedure

- **Tipo di tabella** – AzureFeatureParityResults

  - Utilizzato per contenere i risultati di parità per la valutazione di azure la funzionalità di Azure e passare il AzureFeatureParityResults\_inserire stored procedure

Lo script di PowerShell crea un **elaborati** directory all'interno della directory specificato che contiene i file JSON che devono essere elaborati.

Al termine dell'esecuzione dello script, i risultati vengono importati nella tabella di attività.

### <a name="viewing-the-results-in-sql-server"></a>Visualizzazione dei risultati in SQL Server

Dopo il caricamento dei dati, connettersi all'istanza di SQL Server. Verrà visualizzata una schermata come illustrato nella figura seguente:

![Report consolidati nel database di SQL Server](../dma/media/DMAReportingDatabase.png)

La tabella dbo. Tabella di attività include il contenuto del file JSON in formato non elaborato.

## <a name="on-premises-upgrade-success-ranking"></a>On-premise aggiornare classificazione esito positivo

Per visualizzare un elenco dei database e il numero di dimensioni di successo di percentuale (%), selezionare la tabella dbo. Visualizzazione UpgradeSuccessRanking_OnPrem:

![UpgradeSuccessRaning_OnPrem visualizzazione dei dati](../dma/media/UpgradeSuccessRankingView.png)

Qui è possibile visualizzare per un determinato database qual è la probabilità di successo aggiornamento i livelli di compatibilità diversi. In tal caso, ad esempio, il database delle risorse Umane stato valutato in base a livelli di compatibilità 100, 110, 120 e 130. Questa valutazione consente di vedere visivamente l'impegno è coinvolto esegue la migrazione a una versione successiva di SQL Server dalla versione corrente di cui si trova attualmente il database.

La metrica che è rilevante è in genere sono presenti modifiche di rilievo quanti per un determinato database. Nell'esempio precedente, si noterà che il database delle risorse Umane disponga di un fattore di corretto aggiornamento 50% per i livelli di compatibilità 100, 110, 120 e 130.

Questa metrica può essere influenzata modificando i valori di ponderazione nella tabella dbo. Tabella BreakingChangeWeighting.

Nell'esempio seguente, l'attività di risoluzione del problema di sintassi nel database delle risorse Umane è considerato elevato viene assegnato un valore pari a 3 per **sforzo**. Perché non sarebbe occorrere molto per risolvere il problema di sintassi, viene assegnato un valore pari a 1 **FixTime**. Poiché non vi sarà un costo coinvolti nel apportare la modifica, viene assegnato un valore pari a 2 per **costo**. Utilizzo di questo valore diventa Changerank Blend 2.

> [!NOTE]
> Il punteggio è su una scala da 1 a 5.  1 è il basso e 5 essere elevato. Inoltre, il ChangeRank è una colonna calcolata.

![I valori di impegno, FixTime e costi per il problema di sintassi](../dma/media/SyntaxIssueEffort.png)

Ora in questo esempio, quando si esegue una query la tabella dbo. Visualizzazione UpgradeSuccessRanking_OnPrem, il fattore di corretto aggiornamento del database delle risorse Umane per modifiche di rilievo è eliminato.

![Fattore di successo aggiornamento per i database delle risorse Umane](../dma/media/UpgradeSuccessFactor_HR.png)

## <a name="azure-upgrade-success-ranking"></a>Classificazione di corretto aggiornamento di Azure

Per visualizzare un elenco di database per eseguire la migrazione di database SQL di Azure e il numero di dimensioni di successo di percentuale, selezionare la tabella dbo. Visualizzazione UpgradeSuccessRanking_Azure.

![UpgradeSuccessRanking_Azure visualizzazione dei dati](../dma/media/UpgradeSuccessRankingView_Azure.png)

Di seguito si è interessati nel valore MigrationBlocker. 100,00 significa che vi sia una classificazione di successo 100% per spostare un database in Database SQL di Azure (V12).

La differenza con questa visualizzazione è che non è attualmente alcuna sostituzione per modificare il peso di regole di blocco popup di migrazione.

Per informazioni sulla creazione di report per tali dati con Power BI, vedere [Report consolidate valutazioni con Power BI](../dma/dma-powerbiassesreport.md).
