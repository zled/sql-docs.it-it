---
title: Eseguire la migrazione dello Schema Oracle HR a SQL Server in Linux | Documenti Microsoft
description: Convertire l'esempio di schema Oracle a SQL Server in Linux
author: edmacauley
ms.author: edmacauley
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.suite: sql
ms.custom: ''
ms.technology: database-engine
ms.workload: Inactive
ms.openlocfilehash: db5b4d2d97be21a889257ad990472ee6460ee17a
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="migrate-an-oracle-schema-to-sql-server-2017-on-linux-with-the-sql-server-migration-assistant"></a>Eseguire la migrazione di uno schema Oracle a SQL Server 2017 in Linux con SQL Server Migration Assistant

Questa esercitazione viene utilizzato SQL Server Migration Assistant (SSMA) per Oracle in Windows per convertire il codice di esempio Oracle **HR** schema [2017 di SQL Server in Linux](../../linux/sql-server-linux-overview.md).

> [!div class="checklist"]
> * Scaricare e installare SSMA in Windows
> * Creare un progetto SSMA per gestire la migrazione
> * Connettersi a Oracle
> * Eseguire un report di migrazione
> * Convertire lo schema di esempio delle risorse Umane
> * la migrazione dei dati

## <a name="prerequisites"></a>Prerequisiti

- Un'istanza di Oracle 12C (12.2.0.1.0) con il **HR** installato lo schema
- Un'istanza di lavoro di SQL Server in Linux

> [!NOTE]
> Gli stessi passaggi consentono di destinazione SQL Server in Windows, ma è necessario selezionare Windows nel **Esegui migrazione a** impostazione del progetto.

## <a name="download-and-install-ssma-for-oracle"></a>Scaricare e installare SSMA per Oracle

Sono disponibili varie edizioni di SQL Server Migration Assistant, a seconda del database di origine.  Scaricare la versione corrente di [SQL Server Migration Assistant per Oracle](http://aka.ms/ssmafororacle) e installarlo utilizzando le istruzioni disponibili nella pagina di download.

> [!NOTE]
> In questo momento, il **SSMA per Oracle estensione Pack** non è supportata in Linux, ma non è necessario per questa esercitazione.

## <a name="create-and-set-up-project"></a>Creare e il progetto di installazione

Utilizzare la procedura seguente per creare un nuovo progetto SSMA:

1. Aprire SSMA per Oracle e scegliere **nuovo progetto** dal **File** menu.

1. Assegnare un nome al progetto.

1. Scegliere "SQL Server 2017 (Linux) - anteprima" il **Esegui migrazione a** campo.

SSMA per Oracle non utilizza gli schemi di esempio Oracle per impostazione predefinita. Per abilitare lo schema delle risorse Umane, attenersi alla procedura seguente:

1. SSMA, selezionare il **strumenti** menu.

1. Selezionare **impostazioni di progetto predefinite**, quindi scegliere **durante il caricamento di oggetti di sistema**.

1. Assicurarsi che **HR** è selezionata e scegliere **OK**.

## <a name="connect-to-oracle"></a>Connettersi a Oracle

Riconnette SSMA a Oracle.

1. Sulla barra degli strumenti, fare clic su **Connect to Oracle**.

1. Immettere il nome del server, porta, il SID Oracle, nome utente e password.

   ![Connettersi a Oracle](./media/sql-server-linux-convert-from-oracle/ConnectToOracle.png)

1. quindi fare clic su **Connect**(Connetti). Tra qualche minuto, SSMA per Oracle si connette al database e legge i metadati.

## <a name="create-a-report"></a>Creare un report

Utilizzare la procedura seguente per generare un report di migrazione.

1. Nel **Visualizzatore metadati Oracle**, espandere il nodo del server.

1. Espandere **schemi**, fare doppio clic su **HR**e selezionare **crea Report**.

   ![Visualizzatore metadati Oracle creare Report](./media/sql-server-linux-convert-from-oracle/CreateReport.png)

1. Consente di aprire una nuova finestra del browser con un report che elenca tutti gli avvisi e gli errori associati con la conversione.

   > [!NOTE]
   > Non è necessario eseguire alcuna operazione con tale elenco per questa esercitazione. Se si eseguono questi passaggi per il database Oracle, è necessario esaminare il rapporto per risolvere eventuali problemi di conversione importanti per il database.

   ![Report di migrazione di esempio](./media/sql-server-linux-convert-from-oracle/SSMAReport.png)

## <a name="connect-to-sql-server"></a>Connessione a SQL Server

Scegliere quindi **Connetti al Server SQL** e immettere le informazioni di connessione appropriata.  Se si utilizza un nome di database che non è già esiste, SSMA per Oracle viene creata automaticamente.

![Connessione a SQL Server](./media/sql-server-linux-convert-from-oracle/ConnectToSQLServer.png)

## <a name="convert-schema"></a>Converti Schema

Fare clic su **HR** in **Visualizzatore metadati Oracle**e scegliere Converti Schema.

![Converti Schema](./media/sql-server-linux-convert-from-oracle/ConvertSchema.png)

## <a name="synchronize-database"></a>Sincronizzare Database

Successivamente, eseguire la sincronizzazione del database.

1. Una volta completata la conversione, utilizzare il **Visualizzatore metadati di SQL Server** per passare al database creato nel passaggio precedente.

1. Fare clic sul database, selezionare **Sincronizza con Database**, quindi fare clic su OK.

   ![La sincronizzazione con Database](./media/sql-server-linux-convert-from-oracle/SynchronizeWithDatabase.png)

## <a name="migrate-data"></a>La migrazione dei dati

Il passaggio finale è la migrazione dei dati.

1. Nel **Visualizzatore metadati Oracle**, fare clic su **HR**e selezionare **eseguire la migrazione di dati**.

1. La fase di migrazione dei dati richiede che si nuovamente le credenziali Oracle e SQL Server.

1. Al termine, esaminare il report di migrazione di dati, che dovrebbe essere simile a una schermata riportata di seguito:

   ![Report di migrazione di dati](./media/sql-server-linux-convert-from-oracle/DataMigrationReport.png)

## <a name="next-steps"></a>Passaggi successivi

Per uno schema Orcale più complesso, il processo di conversione comporterebbe più tempo, test e individuare eventuali modifiche alle applicazioni client. Lo scopo di questa esercitazione è mostrare come è possibile utilizzare SSMA per Oracle come parte del processo di migrazione globale.

In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Installare SSMA in Windows
> * Creare un nuovo progetto SSMA
> * Valutare ed eseguire una migrazione da Oracle

Successivamente, è possibile esaminare altri modi per utilizzare SSMA:

> [!div class="nextstepaction"]
>[Documentazione di SQL Server Migration Assistant](../sql-server-migration-assistant.md)
