---
title: Installare e configurare il database di esempio WideWorldImporters - SQL | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: On Demand
ms.openlocfilehash: 3b2a1c4f6fc6045a25a86ea8d49290fafbc29b57
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="installation-and-configuration"></a>Installazione e configurazione
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Wide World Importers OLTP istruzioni di installazione e configurazione del database.

## <a name="prerequisites"></a>Prerequisiti

- [SQL Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) (o versione successiva) o [Database SQL di Azure](https://azure.microsoft.com/services/sql-database/). Per la versione completa dell'esempio, utilizzare SQL Server Evaluation o Developer o Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Per risultati ottimali utilizzano la versione di giugno 2016 o versione successiva.

## <a name="download"></a>Scarica

La versione più recente dell'esempio:

[wide-world-importers-release](http://go.microsoft.com/fwlink/?LinkID=800630)

Scaricare l'esempio WideWorldImporters database backup/bacpac corrispondente per l'edizione di SQL Server o Database SQL di Azure.

Il codice sorgente per ricreare il database di esempio è disponibile dal seguente percorso. Si noti che si ricreano l'esempio genererà piccole differenze nei dati, poiché è un fattore casuale la generazione di dati:

["wide" mondo](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-database-scripts)

## <a name="install"></a>Install


### <a name="sql-server"></a>SQL Server

Per ripristinare un backup a un'istanza di SQL Server, è possibile utilizzare Management Studio.

1. Aprire SQL Server Management Studio e connettersi all'istanza di SQL Server di destinazione.
2. Fare clic su di **database** nodo e selezionare **Restore Database**.
3. Selezionare **dispositivo** e fare clic sul pulsante **...**
4. Nella finestra di dialogo **Seleziona dispositivi di backup**, fare clic su **Aggiungi**, passare al backup del database nel file System del server e selezionare il backup. Scegliere **OK**.
5. Se necessario, modificare il percorso di destinazione per i dati e file di log, nel **file** riquadro. Si noti che è quindi consigliabile inserire i dati e file di registro in unità differenti.
6. Scegliere **OK**. Verrà avviato il ripristino di database. Una volta completato, si disporrà del database WideWorldImporters installati nell'istanza del Server SQL.

### <a name="azure-sql-database"></a>Azure SQL Database

Per importare un file bacpac in un nuovo Database SQL, è possibile utilizzare Management Studio.

1. (facoltativo) Se si non dispone ancora di un Server SQL in Azure, passare al [portale di Azure](https://portal.azure.com/) e creare un nuovo Database SQL. Provvedendo creare un database, si creerà un server. Prendere nota del server.
   - Vedere [questa esercitazione](https://azure.microsoft.com/documentation/articles/sql-database-get-started/) per creare un database in minuti
2. Aprire SQL Server Management Studio e connettersi al server in Azure.
3. Fare clic su di **database** nodo e selezionare **Importa applicazione livello dati**.
4. Nel **importare le impostazioni** selezionare **Importa da disco locale** e selezionare il file bacpac del database di esempio dal file system.
5. In **le impostazioni del Database** modificare il nome del database per *WideWorldImporters* e selezionare l'obiettivo di edizione e il servizio di destinazione da utilizzare.
6. Fare clic su **Avanti** e **fine** per avviare la distribuzione. Si verifica di alcuni minuti in un P1. Se un prezzo inferiore livello desiderata, è consigliabile importare in un nuovo database P1, e quindi modificare il piano tariffario per il livello desiderato.

## <a name="configuration"></a>Configurazione

### <a name="full-text-indexing"></a>Indicizzazione full-text

Il database di esempio può avvalersi di indicizzazione Full-Text. Tuttavia, tale funzionalità non è installata per impostazione predefinita con SQL Server, è necessario selezionarla durante l'installazione di SQL Server (è abilitata per impostazione predefinita nel database di SQL Azure). Pertanto, un passaggio di post-installazione è necessario.

1. In SQL Server Management Studio, connettersi al database WideWorldImporters e aprire una nuova finestra query.
2. Eseguire il comando T-SQL seguente per abilitare l'utilizzo dell'indicizzazione Full-Text nel database:  `EXECUTE Application.Configuration_ApplyFullTextIndexing`


### <a name="sql-server-audit"></a>SQL Server Audit

Si applica a: SQL Server

L'abilitazione del controllo in SQL Server richiede una configurazione del server. Per abilitare il controllo di SQL Server per l'esempio WideWorldImporters, eseguire l'istruzione seguente nel database:

    EXECUTE [Application].[Configuration_ApplyAuditing]

Nel Database di SQL Azure, controllo viene configurato tramite il [portale di Azure](https://portal.azure.com/).

### <a name="row-level-security"></a>Sicurezza a livello di riga

Si applica a: Database SQL di Azure

Sicurezza a livello di riga non è abilitata per impostazione predefinita il download di bacpac di WideWorldImporters. Per abilitare la protezione a livello di riga nel database, eseguire la stored procedure seguente:

    EXECUTE [Application].[Configuration_ApplyAuditing]

