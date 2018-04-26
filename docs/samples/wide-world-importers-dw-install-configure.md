---
title: Database di esempio OLAP WideWorldImporters - installare e configurare - SQL | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql
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
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 69eee1a6460509e70b061583d7a096c2b8293294
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="wideworldimportersdw-installation-and-configuration"></a>WideWorldImportersDW installazione e configurazione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Istruzioni di installazione e configurazione per il database WideWorldImportersDW.

- [SQL Server 2016](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) (o versione successiva) o [Database SQL di Azure](https://azure.microsoft.com/services/sql-database/). Per utilizzare la versione completa dell'esempio, utilizzare SQL Server Evaluation o Developer o Enterprise Edition.
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md). Per risultati ottimali utilizzano la versione di giugno 2016 o versione successiva.

## <a name="download"></a>Scarica

La versione più recente dell'esempio:

[Wide world-importers rilascio](http://go.microsoft.com/fwlink/?LinkID=800630)

Scaricare l'esempio WideWorldImportersDW database backup/bacpac corrispondente per l'edizione di SQL Server o Database SQL di Azure.

Il codice sorgente per ricreare il database di esempio è disponibile dal seguente percorso. Si noti che il popolamento di dati è basato su ETL del database OLTP (WideWorldImporters):

[Wide world-importers source](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-dw-database-scripts)

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
5. In **le impostazioni del Database** modificare il nome del database per *WideWorldImportersDW* e selezionare l'obiettivo di edizione e il servizio di destinazione da utilizzare.
6. Fare clic su **Avanti** e **fine** per avviare la distribuzione. Richiederà alcuni minuti. Quando si specifica un obiettivo di servizio inferiore S2 può richiedere più tempo.

## <a name="configuration"></a>Configurazione

[Si applica a SQL Server 2016 (e versioni successive) Evaluation/Developer o Enterprise Edition]

Il database di esempio può avvalersi di PolyBase per i file di query in Hadoop o Azure nell'archivio blob. Tuttavia, tale funzionalità non è installata per impostazione predefinita con SQL Server, è necessario selezionarla durante l'installazione di SQL Server. Pertanto, un passaggio di post-installazione è necessario.

1. In SQL Server Management Studio, connettersi al database WideWorldImportersDW e aprire una nuova finestra query.
2. Eseguire il comando T-SQL seguente per abilitare l'utilizzo di PolyBase nel database:

   ESEGUIRE [applicazioni]. [Configuration_ApplyPolyBase]
