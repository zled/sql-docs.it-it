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
ms.openlocfilehash: a931ddb3cf3229970de4b301e18002484acbaf53
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
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
- Scaricare i [database campione AdventureWorks2016](https://github.com/Microsoft/sql-server-samples/releases). Le istruzioni per il ripristino dei database in SSMS sono disponibili in [Ripristino di un database](https://docs.microsoft.com/en-us/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms). 


## <a name="script-queries-from-gui"></a>Eseguire script di query dalla GUI
Ogni volta che si esegue un'attività usando la GUI in SSMS, è possibile generare anche il codice T-SQL associato all'attività. Negli esempi seguenti viene illustrato come eseguire questa operazione quando si esegue il backup di un database e quando si compatta il log delle transazioni.  Questi stessi passaggi possono essere applicati a qualsiasi azione che viene completata tramite la GUI. 

### <a name="script-t-sql-when-backing-up-a-database"></a>Generare script T-SQL quando si esegue il backup di un database
1. Connettersi a SQL Server.
2. Espandere il nodo di **Database** .
3. Fare clic con il pulsante destro del mouse sul database **Adventureworks2016** > **Attività** > **Backup**:

    ![Eseguire il backup di un database](media/scripting-ssms/backupdb.png)

4. Configurare il backup in base alle preferenze. Ai fini di questa esercitazione, sono stati lasciati tutti i valori predefiniti. Tuttavia, tutte le modifiche apportate nella finestra si riflettono nello script. 
5. Fare clic sull'opzione **Script** > **Genera script azione in nuova finestra Query**:
 
    ![Generare lo script del backup del database](media/scripting-ssms/scriptdbbackup.PNG)
6. Esaminare il codice T-SQL compilato nella finestra della query: 

    ![Generare lo script per il backup del database](media/scripting-ssms/dbbackupscript.PNG)
7. Selezionare **Esegui** per eseguire la query per il backup del database tramite T-SQL. 


### <a name="script-t-sql-when-shrinking-the-transaction-log"></a>Generare script T-SQL per compattare il log delle transazioni
1. Fare clic con il pulsante destro del mouse sul database **AdventureWorks2016** > **Attività** > **Compatta** > **File**:

     ![Compattare file](media/scripting-ssms/shrinkfiles.png)

2. Selezionare **Log** dall'elenco a discesa **Tipo file**:

    ![Compattare il log delle transazioni](media/scripting-ssms/shrinktlog.png)

3. Selezionare l'opzione **Script** e quindi **Genera script azione negli Appunti**:

    ![Genera script negli Appunti](media/scripting-ssms/scriptactiontoclipboard.png)

4. Aprire una finestra **Nuova query** e incollare facendo clic con il pulsante destro del mouse nella finestra > **Incolla**:

    ![Incollare lo script](media/scripting-ssms/paste.png)
5. Selezionare **Esegui** per eseguire la query e compattare il log delle transazioni. 


## <a name="script-databases"></a>Generare script di database
Nella sezione seguente viene illustrato come generare uno script per un database, sia con l'opzione **Script come** che con l'opzione **Genera script**.  L'opzione **Script come** ricrea il database e le opzioni di configurazione relative. L'opzione **Genera script** consente di eseguire lo script sia dello schema che dei dati. In questa sezione verranno creati due nuovi database. *AdventureWorks2016a* sarà creato usando l'opzione **Script come**, *AdventureWorks2016b* sarà creato usando l'opzione **Genera script**. 


### <a name="script-database-using-script-option"></a>Generare script per database con l'opzione di scripting
1. Connettersi a SQL Server.
2. Espandere il nodo di **Database** .
3. Fare clic con il pulsante destro del mouse sul database **AdventureWorks2016** > **Crea script per database** > **CREATE in** > **Nuova finestra di query**:

    ![Generare script per database](media/scripting-ssms/scriptdb.png)

4. Esaminare la query di creazione del database nella finestra: 

    ![Script del database](media/scripting-ssms/scriptedoutdb.png)
    - Questa opzione consente di generare solo le opzioni di configurazione del database.
5. Sulla tastiera selezionare **CTRL + F** per aprire la finestra di dialogo **Trova** e selezionare la freccia giù per aprire l'opzione **Sostituzione**. Nella riga in alto della finestra **Trova** digitare *AdventureWorks2016* e nella riga inferiore **Sostituzione** digitare *AdventureWorks2016a*. 
6. Selezionare **Replace All** (Sostituisci tutto) per sostituire tutte le istanze di *AdventureWorks2016* con *AdventureWorks2016a*. 

    ![Trova e sostituisci](media/scripting-ssms/findandreplace.png)

1. Selezionare **Esegui** per eseguire la query e creare un nuovo database *AdventureWorks2016a*. 

### <a name="script-database-using-generate-scripts-option"></a>Generare script per database con l'opzione Genera script
1. Connettersi a SQL Server.
2. Espandere il nodo di **Database** .
3. Fare clic con il pulsante destro del mouse sul database **AdventureWorks2016** > **Attività** > **Genera script**:

    ![Generare script per database](media/scripting-ssms/generatescriptsfordb.png)

4. Quando viene aperta la pagina **Introduzione**, selezionare **Successivo** per aprire la pagina **Seleziona oggetti**. È possibile selezionare l'intero database o oggetti specifici del database. Selezionare l'opzione **Genera script per intero database e tutti gli oggetti di database** 
 
    ![Generare script per oggetti](media/scripting-ssms/scriptobjects.png)
 
5. Selezionare **Successivo** per aprire la pagina **Imposta opzioni di generazione script**, da dove è possibile configurare il percorso in cui salvare lo script, nonché alcune opzioni avanzate aggiuntive. 

    A. Selezionare l'opzione **Salva in una nuova finestra Query**. 

    B. Selezionare **Avanzate** e assicurarsi che le opzioni seguenti siano impostate come segue: 

      - **Script per statistiche** impostato su *Genera script per statistiche*
      - **Tipi di dati per cui generare lo script** impostato su *Solo schema*
      - **Script per indici** impostato su *true*

   ![Oggetti dello script](media/scripting-ssms/advancedscripts.png)

   > [!NOTE]
   > È possibile creare lo script di dati per il database quando si seleziona *Schema e dati* per l'opzione **Tipi di dati per cui generare lo script**. Tuttavia, questa opzione non è ideale con database di grandi dimensioni in quanto può richiedere più memoria di quella che SSMS può allocare. È una scelta applicabile per piccoli database, ma se si vogliono spostare dati per database di grandi dimensioni è necessario usare l'[Importazione/esportazione guidata](https://docs.microsoft.com/en-us/sql/integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard).



1. Selezionare **OK** e quindi selezionare **Successivo**. 
2. Selezionare **Successivo** nel **Riepilogo** e quindi selezionare nuovamente **Successivo** per generare lo script in una finestra **Nuova query**.  
3. Sulla tastiera selezionare **CTRL + F** per aprire la finestra di dialogo **Trova** e selezionare la freccia giù per aprire l'opzione **Sostituzione**. Nella riga in alto della finestra **Trova** digitare *AdventureWorks2016* e nella riga inferiore **Sostituzione** digitare *AdventureWorks2016b*. 
    A. Selezionare **Replace All** (Sostituisci tutto) per sostituire tutte le istanze di *AdventureWorks2016* con *AdventureWorks2016b*. 

    ![AdventureWorks2016b](media/scripting-ssms/adventureworks2016b.png)
7. Selezionare **Esegui** per eseguire la query e creare un nuovo database *AdventureWorks2016b*. 
 
## <a name="script-tables"></a>Generare script per tabelle
In questa sezione viene illustrato come generare script di tabelle dal database. Questa opzione consente di creare la tabella o eliminare e creare la tabella. È anche possibile usare questa opzione per creare lo script T-SQL associato modificando la tabella, ad esempio inserendola o aggiornandola al suo interno. In questa sezione verrà eliminata e ricreata una tabella. 

1. Connettersi a SQL Server.
2. Espandere il nodo **Database**.
3. Espandere il nodo del database **AdventureWorks**. 
4. Espandere il nodo **Tabelle**.
5. Fare clic con il pulsante destro del mouse su **dbo.ErrorLog** >  **Crea script per tabella** > **DROP e CREATE in** > **Nuova finestra editor di query**:
    
    ![Creazione di script per tabella](media/scripting-ssms/scripttable.png)

6. Selezionare **Esegui** per eseguire la query. In questo modo la tabella *Errorlog* verrà eliminata e ricreata. 

    >[!NOTE]
    > Per impostazione predefinita, la tabella *Errorlog* del database AdventureWorks2016 è vuota, quindi non verranno persi dati quando la tabella verrà eliminata. Tuttavia, se si segue la procedura con una tabella contenente dati, questi andranno persi. 
 
## <a name="script-stored-procedures"></a>Generare script per stored procedure
In questa sezione verrà eliminata e ricreata una stored procedure.  

1. Connettersi a SQL Server.
2. Espandere il nodo **Database**.
3. Espandere il nodo **Programmabilità**. 
4. Espandere il nodo **Stored procedure**.
5. Fare clic con il pulsante destro del mouse sulla stored procedure **dbo.uspGetBillOfMaterials**> **Crea script per stored procedure** > **DROP e CREATE in** > **Nuova finestra di query**:
    
    ![Generare script per stored procedure](media/scripting-ssms/scriptstoredprocedure.PNG)

## <a name="script-extended-events"></a>Generare script per eventi estesi
In questa sezione viene illustrato come inserire nello script gli [eventi estesi](https://docs.microsoft.com/en-us/sql/relational-databases/extended-events/extended-events). 

1. Connettersi a SQL Server.
2. Espandere il nodo **Gestione**.
3. Espandere il nodo **Eventi estesi**.
4. Espandere il nodo **Sessioni**.
5. Fare clic con il pulsante destro del mouse sulla sessione estesa di interesse > **Crea script per sessione** > **Nuova finestra editor di query**:

    ![Generare script per eventi](media/scripting-ssms/scriptxevents.png) 
6. In **Nuova finestra di query** modificare il nuovo nome della sessione da *system_health* a *system_health2* e selezionare **Esegui** per eseguire la query. 

    A. Fare clic con il pulsante destro del mouse su **Sessioni** in **Esplora oggetti** e selezionare **Aggiorna** per visualizzare la nuova sessione Evento esteso. L'icona verde accanto alla sessione indica che la sessione è in esecuzione mentre l'icona rossa indica che la sessione è stata arrestata. 

    ![Nuovo evento](media/scripting-ssms/newxevent.png)

    >[!NOTE]
    > È possibile avviare la sessione selezionandola con il pulsante destro del mouse e scegliendo **Avvia**. Tuttavia, poiché si tratta di una copia della sessione *system_health* già in esecuzione, questo passaggio può essere ignorato. È possibile eliminare la copia della sessione Evento esteso selezionandola con il pulsante destro del mouse e scegliendo **Elimina**. 

## <a name="next-steps"></a>Passaggi successivi
Nell'articolo successivo verranno illustrati i modelli predefiniti T-SQL disponibili in SSMS. 

Per altre informazioni, vedere l'articolo successivo:
> [!div class="nextstepaction"]
> [Passaggi successivi](templates-ssms.md)


