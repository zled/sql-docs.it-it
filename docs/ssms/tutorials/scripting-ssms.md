---
Title: 'Tutorial: Script Objects in SQL Server Management Studio'
description: Esercitazione per lo scripting di oggetti in SSMS.
keywords: SQL Server, SSMS, SQL Server Management Studio, Script, Scripting
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- projects [SQL Server Management Studio], tutorials
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- solutions [SQL Server Management Studio], tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.openlocfilehash: bc20cc573c6b0890e5b16f4876636534f9fbb916
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-script-objects-in-sql-server-management-studio"></a>Esercitazione: Eseguire script per oggetti in SQL Server Management Studio
In questa esercitazione viene illustrato come generare script Transact-SQL (T-SQL) per vari oggetti presenti in SQL Server Management Studio.  In questa esercitazione è possibile trovare esempi di come creare script per gli oggetti seguenti: 

> [!div class="checklist"]
> * Query durante l'esecuzione di azioni all'interno della GUI
> * Database in due modalità diverse ("Script come" e "Genera Script")
> * Tabelle
> * Stored procedure
> * Eventi estesi

Il sunto di questa esercitazione è che è possibile inserire in uno script qualsiasi oggetto presente in **Esplora oggetti** selezionandolo con il pulsante destro del mouse e scegliendo l'opzione **Script Object As** (Crea script per oggetto). 


## <a name="prerequisites"></a>Prerequisites
Per completare questa esercitazione, sono necessari SQL Server Management Studio, l'accesso a SQL Server e un database AdventureWorks. 

- Installare [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Installare [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).
- Scaricare un [database campione AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases). Le istruzioni per il ripristino dei database in SSMS sono disponibili in [Ripristino di un database](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 


## <a name="script-queries-from-gui"></a>Eseguire script di query dalla GUI
Ogni volta che si esegue un'attività usando la GUI in SSMS, è possibile generare anche il codice T-SQL associato all'attività. Negli esempi seguenti viene illustrato come eseguire questa operazione quando si esegue il backup di un database e quando si compatta il log delle transazioni.  Questi stessi passaggi possono essere applicati a qualsiasi azione che viene completata tramite la GUI. 

### <a name="script-t-sql-when-backing-up-a-database"></a>Generare script T-SQL quando si esegue il backup di un database
1. Connettersi a SQL Server.
2. Espandere il nodo di **Database** .
3. Fare clic con il pulsante destro del mouse sul database > **Attività** > **Back up** (Esegui backup):

    ![Eseguire il backup di un database](media/scripting-ssms/backupdb.png)

4. Configurare il backup in base alle preferenze. Ai fini di questa esercitazione, sono stati lasciati tutti i valori predefiniti. Tuttavia, tutte le modifiche apportate nella finestra si riflettono nello script. 
5. Fare clic sull'opzione **Script** > **Genera script azione in nuova finestra Query**:
 
    ![Generare lo script del backup del database](media/scripting-ssms/scriptdbbackup.PNG)
6. Esaminare il codice T-SQL compilato nella finestra della query: 

    ![Generare lo script per il backup del database](media/scripting-ssms/dbbackupscript.PNG)


### <a name="script-t-sql-when-shrinking-the-transaction-log"></a>Generare script T-SQL per compattare il log delle transazioni
1. Fare clic con il pulsante destro del mouse sul database > **Attività** > **Compatta** > **File**:

     ![Compattare file](media/scripting-ssms/shrinkfiles.png)

2. Selezionare **Log** dall'elenco a discesa **Tipo file**:

    ![Compattare il log delle transazioni](media/scripting-ssms/shrinktlog.png)

3. Fare clic sull'opzione **Script** e **Genera script azione negli Appunti**:

    ![Genera script negli Appunti](media/scripting-ssms/scriptactiontoclipboard.png)

4. Aprire una finestra **Nuova query** e incollare (fare clic con il pulsante destro del mouse nella finestra > **Incolla**):

    ![Incollare lo script](media/scripting-ssms/paste.png)


## <a name="script-databases"></a>Generare script di database
Nella sezione seguente viene illustrato come generare uno script per un database, sia con l'opzione **Script come** che con l'opzione **Genera script**.  L'opzione **Script come** ricrea il database e le opzioni di configurazione relative. L'opzione **Genera script** crea uno script contenente tutti gli oggetti nel database, ma non i dati. Per creare uno script che includa anche i dati, è necessario usare [Importazione/esportazione guidata](https://docs.microsoft.com/en-us/sql/integration-services/import-export-data/start-the-sql-server-import-and-export-wizard).  


### <a name="script-database-using-script-option"></a>Generare script per database con l'opzione di scripting
1. Connettersi a SQL Server.
2. Espandere il nodo di **Database** .
3. Fare clic con il pulsante destro del mouse sul database > **Crea script per database**:

    ![Generare script per database](media/scripting-ssms/scriptdb.png)

4. Esaminare la query di creazione del database nella finestra: 

    ![Script del database](media/scripting-ssms/scriptedoutdb.png)
    - Questa opzione consente di generare solo le opzioni di configurazione del database.  

### <a name="script-database-using-generate-scripts-option"></a>Generare script per database con l'opzione Genera script
1. Connettersi a SQL Server.
2. Espandere il nodo di **Database** .
3. Fare clic con il pulsante destro del mouse sul database > **Attività** > **Genera script**:

    ![Generare script per database](media/scripting-ssms/generatescriptsfordb.png)

4. Selezionare **Avanti** e si noterà che è possibile scegliere di inserire nello script l'intero database oppure oggetti specifici all'interno del database: 
 
    ![Generare script per oggetti](media/scripting-ssms/scriptobjects.png)
 
5. Fare clic su **Avanti**. Da questa schermata è possibile configurare il percorso in cui verrà salvato lo script. 
    - È anche possibile configurare le opzioni avanzate selezionando **Avanzate**:

    ![Opzioni di generazione script avanzate](media/scripting-ssms/advancedscripts.png)

6. Quando si vuole procedere, premere **Avanti** fino a quando non vengono generati gli script e si arriva alla **Fine**. Lo script del database si troverà nel percorso in cui è stato salvato nel passaggio 5. 
    - In questo modo verrà creato lo script dello schema e dei vari oggetti all'interno del database, ma non dei dati. 
 
## <a name="script-tables"></a>Generare script per tabelle
In questa sezione viene illustrato come generare script di tabelle dal database.

1. Connettersi a SQL Server.
2. Espandere il nodo **Database**.
3. Espandere il nodo del database **AdventureWorks**. 
4. Espandere il nodo **Tabelle**.
5. Fare clic con il pulsante destro del mouse sulla tabella da inserire nello script > **Crea script per tabella**:
    - A questo punto sono disponibili diverse opzioni, come ad esempio la creazione della tabella o l'inserimento di dati al suo interno: 
    
    ![Creazione di script per tabella](media/scripting-ssms/scripttable.png)
 
## <a name="script-stored-procedures"></a>Generare script per stored procedure
In questa sezione viene illustrato come inserire nello script le stored procedure. 

1. Connettersi a SQL Server.
2. Espandere il nodo **Database**.
3. Espandere il nodo **Programmabilità**. 
4. Espandere il nodo **Stored procedure**.
5. Fare clic con il pulsante destro del mouse sulla stored procedure di interesse > **Crea script per stored procedure**:
    
    ![Generare script per stored procedure](media/scripting-ssms/scriptstoredprocedure.PNG)

## <a name="script-extended-events"></a>Generare script per eventi estesi
In questa sezione viene illustrato come inserire nello script gli [eventi estesi](https://docs.microsoft.com/en-us/sql/relational-databases/extended-events/extended-events). 

1. Connettersi a SQL Server.
2. Espandere il nodo **Gestione**.
3. Espandere il nodo **Eventi estesi**.
4. Espandere il nodo **Sessioni**.
5. Fare clic con il pulsante destro del mouse sulla sessione estesa di interesse > **Crea script per sessione**:

    ![Generare script per eventi](media/scripting-ssms/scriptxevents.png) 

## <a name="next-steps"></a>Passaggi successivi
Nell'articolo successivo verranno illustrati i modelli predefiniti disponibili in SSMS. 

Per altre informazioni, vedere l'articolo successivo
> [!div class="nextstepaction"]
> [Pulsante passaggi successivi](templates-ssms.md)


