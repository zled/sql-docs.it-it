---
title: Il caricamento di convertire gli oggetti di Database in SQL Server (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ac993a6d-0283-4823-8793-6b217677dfa3
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cc70aebab39bc1d60f6b6e933f53d9f32cb87d6e
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="loading-converted-database-objects-into-sql-server-mysqltosql"></a>Il caricamento di convertire gli oggetti di Database in SQL Server (MySQLToSQL)
Dopo aver convertito i database MySQL per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è possibile caricare gli oggetti di database risultante in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È possibile avere SSMA creare gli oggetti, oppure è possibile creare script degli oggetti ed eseguire gli script manualmente. SSMA consente inoltre di aggiornare i metadati di destinazione con il contenuto effettivo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Scelta tra sincronizzazione e gli script  
Se si desidera caricare gli oggetti di database convertito in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure senza modifiche, è possibile avere SSMA direttamente a creare o ricreare gli oggetti di database. Metodo è rapido e semplice che non consente la personalizzazione del codice Transact-SQL che definisce il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di SQL Azure.  
  
Se si desidera modificare Transact-SQL che viene utilizzato per creare oggetti o se si desidera maggiore controllo sulla creazione di oggetti, utilizzare SSMA per creare script. È possibile quindi modificare questi script, creare singolarmente ogni oggetto e anche utilizzare SQL Server Agent per pianificare la creazione di questi oggetti.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Utilizzo di SSMA per sincronizzare gli oggetti con SQL Server  
Per utilizzare SSMA per creare oggetti di database di SQL Server o SQL Azure, si seleziona gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure e quindi sincronizzare gli oggetti con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, come illustrato nella procedura seguente. Per impostazione predefinita, se gli oggetti esistono già nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e se i metadati SSMA alcune modifiche locali o gli aggiornamenti alla definizione di tali oggetti molto, allora SSMA modificherà le definizioni degli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È possibile modificare il comportamento predefinito modificando **impostazioni progetto**.  
  
> [!NOTE]  
> È possibile selezionare esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di database SQL Azure non sono stati convertiti dal database MySQL. Tuttavia, questi oggetti non verrà ricreati o modificati da SSMA.  
  
##### <a name="to-synchronize-objects-with-sql-server-or-sql-azure"></a>Per sincronizzare gli oggetti con SQL Server o SQL Azure  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati di SQL Azure, espandere la parte superiore o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o nodo di SQL Azure, quindi espandere **database**.  
  
2.  Selezionare gli oggetti da elaborare:  
  
    -   Per sincronizzare un database completo, selezionare la casella di controllo accanto al nome del database.  
  
    -   Per sincronizzare o omettere i singoli oggetti o le categorie di oggetti, selezionare o deselezionare la casella di controllo accanto all'oggetto o una cartella.  
  
3.  Dopo aver selezionato gli oggetti da elaborare in SQL Server o Visualizzatore metadati di SQL Azure, fare doppio clic su **database**, quindi fare clic su **Sincronizza con Database**.  
  
    È inoltre possibile sincronizzare oggetti singoli o le categorie di oggetti facendo clic l'oggetto o la relativa cartella padre, e quindi fare clic su **Sincronizza con Database**.  
  
    Successivamente, verrà visualizzato SSMA il **Sincronizza con Database** finestra di dialogo, in cui è possibile visualizzare due gruppi di elementi. Sul lato sinistro, SSMA viene rappresentati in un albero di oggetti di database selezionati. Sul lato destro, è possibile visualizzare una struttura ad albero che rappresentano gli stessi oggetti di metadati SSMA. È possibile espandere l'albero facendo clic sulla destra o sinistra pulsante ' +'. La direzione della sincronizzazione è visualizzata nella colonna azione inserita tra i due alberi.  
  
    Un segno di azione può trovarsi in tre stati seguenti:  
  
    -   Una freccia a sinistra, significa che verrà salvato il contenuto dei metadati del database (predefinito).  
  
    -   Una freccia a destra significa che il contenuto di database sovrascriverà i metadati SSMA.  
  
    -   Una croce, significa che verrà intrapresa alcuna azione.  
  
    -   Fare clic sul segno di azione di modifica dello stato. Sincronizzazione effettiva verrà eseguita quando si fa clic **OK** pulsante il **Sincronizza con Database** finestra di dialogo.  
  
## <a name="scripting-objects"></a>Oggetti di scripting  
Per salvare [!INCLUDE[tsql](../../includes/tsql_md.md)] le definizioni degli oggetti di database convertito, o per modificare le definizioni degli oggetti ed eseguire gli script manualmente, è possibile salvare il database convertito definizioni di oggetto [!INCLUDE[tsql](../../includes/tsql_md.md)] script.  
  
**Per salvare gli oggetti script**  
  
1.  Dopo aver selezionato gli oggetti per salvare uno script, fare doppio clic su **database**, quindi fare clic su **salvare come Script**.  
  
    È inoltre possibile generare script singoli oggetti o le categorie di oggetti facendo clic l'oggetto o la relativa cartella padre, e quindi fare clic su **salvare come Script**.  
  
2.  Nel **Salva con nome** finestra di dialogo, individuare la cartella in cui si desidera salvare lo script, immettere un nome di file nel **nome File** casella, quindi [!INCLUDE[clickOK](../../includes/clickok_md.md)] SSMA aggiungerà l'estensione del nome file con estensione SQL.  
  
### <a name="modifying-scripts"></a>Modifica di script  
Dopo aver salvato come script di SQL Server o le definizioni degli oggetti di SQL Azure, è possibile utilizzare SQL Server Management Studio per modificare lo script.  
  
**Per modificare uno script**  
  
1.  In Management Studio **File** dal menu **aprire**, quindi fare clic su **File**.  
  
2.  Nella finestra di dialogo aperte, individuare e selezionare il file di script e quindi fare clic su **OK**.  
  
3.  Modificare il file di script tramite l'editor di query. Per ulteriori informazioni sull'editor di query, vedere "Editor comandi e funzionalità comode" nella documentazione Online di SQL Server.  
  
4.  Per salvare lo script, dal menu File, selezionare **salvare**.  
  
### <a name="running-scripts"></a>Esecuzione di script  
È possibile eseguire uno script o singole istruzioni, in SQL Server Management Studio.  
  
**Per eseguire uno script**  
  
1.  In SQL Server Management Studio **File** dal menu **aprire** e quindi fare clic su **File**.  
  
2.  Nella finestra di dialogo aperte, individuare e selezionare il file di script e quindi fare clic su **OK**.  
  
3.  Per eseguire lo script completo, premere il **F5** chiave.  
  
4.  Per eseguire un set di istruzioni, selezionare le istruzioni nella finestra dell'editor di query e quindi premere il **F5** chiave.  
  
5.  Per ulteriori informazioni su come usare l'editor di query per eseguire gli script, vedere "SQL Server Management Studio Query Transact-SQL" nella documentazione Online di SQL Server.  
  
6.  È inoltre possibile eseguire script dalla riga di comando utilizzando il **sqlcmd** e utilità di SQL Server Agent. Per ulteriori informazioni su **sqlcmd**, vedere "utilità sqlcmd" nella documentazione Online di SQL Server. Per ulteriori informazioni su SQL Server Agent, vedere "Automatizzare attività amministrative (SQL Server Agent)" nella documentazione Online di SQL Server.  
  
## <a name="securing-objects-in-sql-server"></a>Protezione degli oggetti in SQL Server  
Dopo aver caricato gli oggetti di database convertito in SQL Server, è possibile concedere e negare autorizzazioni per tali oggetti. È consigliabile eseguire questa operazione prima della migrazione di dati in SQL Server. Per informazioni su come migliorare la protezioni di oggetti in SQL Server, vedere "Protezione considerazioni per i database e applicazioni di Database" nella documentazione Online di SQL Server.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione è [la migrazione dei dati di MySQL in SQL Server - database SQL di Azure &#40; MySQLToSQL &#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database MySQL a SQL Server: database SQL di Azure &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
