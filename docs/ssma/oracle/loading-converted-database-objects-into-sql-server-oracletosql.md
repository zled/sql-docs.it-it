---
title: Il caricamento di convertire gli oggetti di Database in SQL Server (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Synchronization, Securing Objects in SQL Server
- Synchronization,Scripting Objects
ms.assetid: a8ae33b2-1883-4785-922b-ea0e31c0b37a
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6fd5616c61af419d5d2ff3134177ae296b317d57
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="loading-converted-database-objects-into-sql-server-oracletosql"></a>Il caricamento di convertire gli oggetti di Database in SQL Server (OracleToSQL)
Dopo aver convertito schemi Oracle a SQL Server, è possibile caricare gli oggetti di database risultante in SQL Server. È possibile avere SSMA creare gli oggetti, oppure è possibile creare script degli oggetti ed eseguire gli script manualmente. SSMA consente inoltre di aggiornare i metadati di destinazione con il contenuto effettivo del database di SQL Server.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Scelta tra sincronizzazione e gli script  
Se si desidera caricare gli oggetti di database convertito in SQL Server senza alcuna modifica, è possibile fare SSMA direttamente a creare o ricreare gli oggetti di database. Metodo è rapido e semplice che non consentono la personalizzazione del [!INCLUDE[tsql](../../includes/tsql_md.md)] codice che definisce gli oggetti di SQL Server, diverso da stored procedure.  
  
Se si desidera modificare il [!INCLUDE[tsql](../../includes/tsql_md.md)] utilizzato per creare oggetti o se si desidera maggiore controllo sulla creazione di oggetti, l'uso di SSMA per creare script. È possibile quindi modificare gli script, creare singolarmente ogni oggetto e anche utilizzare SQL Server Agent per pianificare la creazione di tali oggetti.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Utilizzo di SSMA per sincronizzare gli oggetti con SQL Server  
Per utilizzare SSMA per creare oggetti di database di SQL Server, selezionare gli oggetti in Visualizzatore metadati di SQL Server e quindi sincronizzare gli oggetti con SQL Server, come illustrato nella procedura seguente. Per impostazione predefinita, se gli oggetti esistono già in SQL Server e se i metadati SSMA sono più recenti di SQL Server, l'oggetto SSMA modificherà le definizioni degli oggetti in SQL Server. È possibile modificare il comportamento predefinito modificando **impostazioni progetto**.  
  
> [!NOTE]  
> È possibile selezionare oggetti di database di SQL Server esistenti che non sono stati convertiti dal database Oracle. Tuttavia, tali oggetti non verrà ricreati o modificati da SSMA.  
  
**Per sincronizzare gli oggetti con SQL Server**  
  
1.  In Esplora i metadati di SQL Server, espandere il nodo principale di SQL Server e quindi espandere **database**.  
  
2.  Selezionare gli oggetti da elaborare:  
  
    -   Per sincronizzare un database completo, selezionare la casella di controllo accanto al nome del database.  
  
    -   Per sincronizzare o omettere i singoli oggetti o le categorie di oggetti, selezionare o deselezionare la casella di controllo accanto all'oggetto o una cartella.  
  
3.  Dopo aver selezionato gli oggetti da elaborare in Visualizzatore metadati di SQL Server, fare doppio clic su **database**, quindi fare clic su **Sincronizza con Database**.  
  
    È inoltre possibile sincronizzare oggetti singoli o le categorie di oggetti facendo clic l'oggetto o la relativa cartella padre, e quindi fare clic su **Sincronizza con Database**.  
  
    Successivamente, verrà visualizzato SSMA il **Sincronizza con Database** finestra di dialogo, in cui è possibile visualizzare due gruppi di elementi. Sul lato sinistro, SSMA viene rappresentati in un albero di oggetti di database selezionati. Sul lato destro, è possibile visualizzare una struttura ad albero che rappresentano gli stessi oggetti di metadati SSMA. È possibile espandere l'albero facendo clic sulla destra o sinistra pulsante ' +'. La direzione della sincronizzazione è visualizzata nella colonna azione inserita tra i due alberi.  
  
    Un segno di azione può trovarsi in tre stati:  
  
    -   Una freccia a sinistra, significa che verrà salvato il contenuto dei metadati del database (predefinito).  
  
    -   Una freccia a destra significa che il contenuto di database sovrascriverà i metadati SSMA.  
  
    -   Una croce, significa che verrà intrapresa alcuna azione.  
  
Fare clic sul segno di azione di modifica dello stato. Sincronizzazione effettiva verrà eseguita quando si fa clic **OK** pulsante il **Sincronizza con Database** finestra di dialogo.  
  
## <a name="scripting-objects"></a>Oggetti di scripting  
Per salvare [!INCLUDE[tsql](../../includes/tsql_md.md)] le definizioni degli oggetti di database convertito, o per modificare le definizioni degli oggetti ed eseguire gli script manualmente, è possibile salvare il database convertito definizioni di oggetto [!INCLUDE[tsql](../../includes/tsql_md.md)] script.  
  
**Per salvare gli oggetti script**  
  
1.  Dopo aver selezionato gli oggetti per salvare uno script, fare doppio clic su **database**, quindi fare clic su **salvare come Script**.  
  
    È inoltre possibile generare script singoli oggetti o le categorie di oggetti facendo clic l'oggetto o la relativa cartella padre, e quindi fare clic su **salvare come Script**.  
  
2.  Nel **Salva con nome** finestra di dialogo, individuare la cartella in cui si desidera salvare lo script, immettere un nome di file nel **nome File** casella e quindi fare clic su OK SSMA aggiungerà l'estensione del nome file con estensione SQL.  
  
### <a name="modifying-scripts"></a>Modifica di script  
Dopo aver salvato le definizioni degli oggetti di SQL Server come uno o più script, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] per visualizzare e modificare gli script.  
  
**Per modificare uno script**  
  
1.  Nel [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **File** dal menu **aprire**, quindi fare clic su **File**.  
  
2.  Nel **aprire** la finestra di dialogo, selezionare il file di script, quindi fare clic su OK.
  
3.  Modificare il file di script tramite l'editor di query.  
  
    Per ulteriori informazioni sull'editor di query, vedere "Editor comandi e funzionalità comode" nella documentazione Online di SQL Server.  
  
4.  Per salvare lo script, fare clic su menu File **salvare**.  
  
### <a name="running-scripts"></a>Esecuzione di script  
È possibile eseguire in uno script o singole istruzioni, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Per eseguire uno script**  
  
1.  Nel [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **File** dal menu **aprire**, quindi fare clic su **File**.  
  
2.  Nel **aprire** la finestra di dialogo, selezionare il file di script e quindi fare clic su OK  
  
3.  Per eseguire lo script completo, premere il **F5** chiave.  
  
4.  Per eseguire un set di istruzioni, selezionare le istruzioni nella finestra dell'editor di query e quindi premere il **F5** chiave.  
  
Per ulteriori informazioni su come usare l'editor di query per eseguire gli script, vedere "[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)] Query" nella documentazione Online di SQL Server.  
  
È inoltre possibile eseguire script dalla riga di comando utilizzando il **sqlcmd** utilità e da SQL Server Agent. Per ulteriori informazioni su **sqlcmd**, vedere "utilità sqlcmd" nella documentazione Online di SQL Server. Per ulteriori informazioni su SQL Server Agent, vedere "Automatizzare attività amministrative (SQL Server Agent)" nella documentazione Online di SQL Server.  
  
## <a name="securing-objects-in-sql-server"></a>Protezione degli oggetti in SQL Server  
Dopo aver caricato gli oggetti di database convertito in SQL Server, è possibile concedere e negare autorizzazioni per tali oggetti. È consigliabile eseguire questa operazione prima della migrazione di dati in SQL Server. Per informazioni su come migliorare la protezioni di oggetti in SQL Server, vedere "Protezione considerazioni per i database e applicazioni di Database" nella documentazione Online di SQL Server.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste nel [la migrazione dei dati in SQL Server](http://msdn.microsoft.com/en-us/e23c5268-41ed-4e55-9fe7-a11376202a13).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Oracle a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  

