---
title: Backup e ripristino di un database tramite Studio operazioni SQL (anteprima) | Documenti Microsoft
description: Informazioni su come eseguire il backup e ripristino di un database utilizzando Studio operazioni SQL (anteprima)
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46ef55aa54275e356eff9674aac10a27b36d758e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="backup-and-restore-using-includename-sosincludesname-sos-shortmd"></a>Backup e ripristino mediante[!INCLUDE[name-sos](../includes/name-sos-short.md)]

In questa esercitazione imparare a usare [!INCLUDE[name-sos](../includes/name-sos-short.md)] per:
> [!div class="checklist"]
> * Backup di un database 
> * Visualizzare lo stato del backup
> * Generare lo script utilizzato per eseguire il backup
> * Ripristinare un database
> * Visualizzare lo stato dell'attività di ripristino

## <a name="prerequisites"></a>Prerequisites

In questa esercitazione richiede SQL Server *TutorialDB*. Per creare il *TutorialDB* del database, completare una delle Guide rapide seguenti:

- [Connettersi ed eseguire query tramite SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)


## <a name="backup-a-database"></a>Backup di un database

1. Aprire il dashboard di database TutorialDB (aprire il **server** barra laterale (**CTRL + G**), espandere **database**, fare doppio clic su **TutorialDB**, e selezionare **Gestisci**). 

2. Aprire il **Backup database** finestra di dialogo (fare clic su **Backup** sul **attività** widget).

   ![Widget di attività](./media/tutorial-backup-restore-sql-server/tasks.png)

3. In questa esercitazione Usa le opzioni di backup predefinito, quindi fare clic su **Backup**.
   ![finestra di dialogo backup](./media/tutorial-backup-restore-sql-server/backup-dialog.png)

Dopo aver fatto clic **Backup**, **Backup database** finestra di dialogo viene chiusa e inizia il processo di backup.

## <a name="view-the-backup-status-and-view-the-backup-script"></a>Visualizzare lo stato del backup e lo script di backup

1. Aprire il **Cronologia attività** barra laterale scegliendo l'icona di orologio il *barra delle azioni* o premere **CTRL + T**.

   ![Cronologia attività](./media/tutorial-backup-restore-sql-server/task-history.png)

2. Per visualizzare lo script di backup nell'editor, fare doppio clic su **Database di Backup ha avuto esito positivo** e selezionare **Script**.

   ![script di backup](./media/tutorial-backup-restore-sql-server/task-script.png) 

## <a name="restore-a-database-from-a-backup-file"></a>Ripristinare un database da un file di backup


1. Aprire il **server** barra laterale (**CTRL + G**), il server e scegliere **Gestisci**. 

2. Aprire il **ripristinare il database** finestra di dialogo (fare clic su **ripristinare** sul **attività** widget).

2. Selezionare **file di Backup** nel **ripristino** campo. 

3. Fare clic sui puntini di sospensione (...) nei **percorso file di Backup** campo e selezionare il file di backup più recente per *TutorialDB*.

3. Tipo **TutorialDB_Restored** nel **database di destinazione** campo il **destinazione** sezione per ripristinare il file di backup in un nuovo database.

   ![ripristino](./media/tutorial-backup-restore-sql-server/restore.png)

4. Fare clic su **ripristino**

5. Per visualizzare lo stato dell'operazione di ripristino, fare clic su **CTRL + T** per aprire la **Cronologia attività** barra laterale.

   ![ripristino](./media/tutorial-backup-restore-sql-server/task-history-restore.png)


In questa esercitazione, si è appreso come:
> [!div class="checklist"]
> * Backup di un database 
> * Visualizzare lo stato del backup
> * Generare lo script utilizzato per eseguire il backup
> * Ripristinare un database
> * Visualizzare lo stato dell'attività di ripristino

