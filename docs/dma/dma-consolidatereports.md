---
title: Importare e consolidare i report di valutazione Data Migration Assistant (SQL Server) | Microsoft Docs
description: Informazioni su come importare i report di valutazione da Data Migration Assistant in un database di SQL Server e di consolidare più report
ms.custom: ''
ms.date: 04/16/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: be9fc224093f0d5ae14372d4674a52589a2d4801
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/04/2018
ms.locfileid: "37781772"
---
# <a name="import-and-consolidate-data-migration-assistant-assessment-reports"></a>Importare e consolidare i report di valutazione Data Migration Assistant

È possibile usare la riga di comando per eseguire valutazioni della migrazione in modalità automatica, a partire da v2.1 Data Migration Assistant. Questa funzionalità consente di eseguire le valutazioni su larga scala. I risultati della valutazione sotto forma di un file JSON o CSV.

È possibile valutare più database in un'unica istanza dell'utilità della riga di comando Data Migration Assistant ed esportare tutti i risultati delle valutazioni in un singolo file JSON. In alternativa, è possibile valutare un database in esecuzione e consolidare in un secondo momento i risultati di questi più file JSON in un database SQL.

Per informazioni su come eseguire Data Migration Assistant dalla riga di comando, vedere [eseguito Data Migration Assistant da riga di comando](../dma/dma-commandline.md). 

## <a name="import-assessment-results-into-a-sql-server-database"></a>Importare i risultati della valutazione in un database di SQL Server

Usare lo script di PowerShell disponibile in questo [repository Github](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/data-migration-assistant) per importare i risultati della valutazione dai file JSON in un database di SQL Server.

> [!NOTE]
> PowerShell versione 5 o versione successiva è obbligatorio.

Quando si esegue lo script, è necessario fornire le informazioni seguenti: 

- **serverName**: nome di istanza di SQL Server che si desidera importare la valutazione dei risultati dai file JSON.

- **databaseName**: il nome del database che i risultati vengono importati a.

- **jsonDirectory**: cartella in cui salvare i risultati della valutazione, in uno o più file JSON.

- **processTo**: SQL Server

Aggiungere i valori precedenti nella sezione "Eseguire funzioni", come indicato di seguito.

```
dmaProcessor -serverName localhost \`\
-databaseName DMAReporting \`\
-jsonDirectory "C:\\temp\\DMACmd\\output\\" \`\
-processTo SQLServer
```

Lo script di PowerShell crea gli oggetti seguenti nell'istanza SQL specificata, se gli oggetti non esistono già:

- **Database** : il nome fornito nei parametri di PowerShell

  - Repository principale

- **Tabella** – dati rapporto

  - Dati per reporting

- **Tabella** -BreakingChangeWeighting

  - Tabella di riferimento per tutte le modifiche di rilievo. Qui è possibile definire i propri valori di ponderazione per poter influire sulla classificazione corretto aggiornamento percentuale (%) più accurata.

- **Vista** – UpgradeSuccessRanking\_OnPrem

  - Visualizzazione con un fattore di successo per ogni database sia stata eseguita la migrazione in locale.

- **Vista** – UpgradeSuccessRanking\_Azure

  - Visualizzazione con un fattore di successo per ogni database sia stata eseguita la migrazione in locale.

- **Stored Procedure** – JSONResults\_Insert

  - Utilizzato per importare dati da un file JSON in SQL Server.

- **Stored Procedure** – AzureFeatureParityResults\_Insert

  - Utilizzato per importare i risultati di parità di funzionalità di Azure da un file JSON in SQL Server.

- **Tipo di tabella** – JSONResults

  - Usato per contenere i risultati JSON per le valutazioni in locale e passare al JSONResults\_stored procedure Insert

- **Tipo di tabella** – AzureFeatureParityResults

  - Usato per contenere i risultati di parità per la valutazione di azure la funzionalità di Azure e passare al AzureFeatureParityResults\_stored procedure Insert

Lo script di PowerShell crea una **elaborati** directory all'interno della directory specificato che contiene i file JSON che devono essere elaborate.

Al termine dell'esecuzione dello script, i risultati vengono importati nella tabella, dati rapporto.

### <a name="viewing-the-results-in-sql-server"></a>Visualizzazione dei risultati in SQL Server

Dopo il caricamento di dati, connettersi all'istanza di SQL Server. Verrà visualizzata una schermata come mostrato nella figura seguente:

![Report consolidati nel database di SQL Server](../dma/media/DMAReportingDatabase.png)

La tabella dbo. Tabella dati rapporto include il contenuto del file JSON in formato non elaborato.

## <a name="on-premises-upgrade-success-ranking"></a>In locale aggiornare il rango di esito positivo

Per visualizzare un elenco dei database e dal numero di dimensioni di successo di percentuale (%), selezionare la tabella dbo. Visualizzazione UpgradeSuccessRanking_OnPrem:

![Dati in visualizzazione UpgradeSuccessRaning_OnPrem](../dma/media/UpgradeSuccessRankingView.png)

Qui è possibile visualizzare per un determinato database qual è la probabilità di successo aggiornamento per i livelli di compatibilità diverso. Quindi, ad esempio, il database delle risorse Umane è stato valutato in base a livelli di compatibilità 100, 110, 120 e 130. Questa valutazione consente di visualizzare quantità sforzo implica la migrazione a una versione successiva di SQL Server dalla versione corrente che il database è attualmente in.

La metrica che si è interessati è in genere sono presenti modifiche di rilievo quanti per un determinato database. Nell'esempio precedente, si noterà che il database delle risorse Umane disponga di un fattore di corretto aggiornamento del 50% per i livelli di compatibilità 100, 110, 120 e 130.

Questa metrica può essere influenzata modificando i valori di ponderazione nella tabella dbo. Tabella BreakingChangeWeighting.

Nell'esempio seguente, l'impegno a correggere il problema di sintassi nel database delle risorse Umane è considerato elevato in modo che un valore pari a 3 viene assegnato a **sforzo**. Perché non sarebbe richiedere lungo per risolvere il problema di sintassi, viene assegnato un valore pari a 1 per **FixTime**. Poiché non vi sarà un costo coinvolti nel apportare la modifica, viene assegnato un valore pari a 2 per **costo**. Utilizzo di questo valore diventa il Changerank combinata 2.

> [!NOTE]
> L'assegnazione dei punteggi è su una scala da 1 a 5.  1 è bassa e 5 elevato. Inoltre, il ChangeRank è una colonna calcolata.

![I valori di attività, FixTime e costi per problema di sintassi](../dma/media/SyntaxIssueEffort.png)

Ora disponibile in questo esempio, quando si esegue una query della tabella dbo. Visualizzazione UpgradeSuccessRanking_OnPrem, il fattore di corretto aggiornamento del database delle risorse Umane per modifiche di rilievo è eliminato.

![Fattore di successo di aggiornamento per i database delle risorse Umane](../dma/media/UpgradeSuccessFactor_HR.png)

## <a name="azure-upgrade-success-ranking"></a>Classificazione di Azure aggiornamento completato

Per visualizzare un elenco di database per eseguire la migrazione al database SQL di Azure e dal numero di dimensioni di successo di percentuale, selezionare la tabella dbo. Visualizzazione UpgradeSuccessRanking_Azure.

![Dati in visualizzazione UpgradeSuccessRanking_Azure](../dma/media/UpgradeSuccessRankingView_Azure.png)

Qui si è interessati al valore MigrationBlocker. 100,00 significa che vi sia una classificazione di successo di 100% per lo spostamento di un database alla versione 12 del Database SQL di Azure.

La differenza con questa visualizzazione è che non è attualmente alcun override per modificare la ponderazione per le regole di blocco della migrazione.

Per informazioni sulla funzionalità di segnalazione in merito ai dati tramite Power BI, vedere [segnalare le valutazioni consolidate con Power BI](../dma/dma-powerbiassesreport.md).
