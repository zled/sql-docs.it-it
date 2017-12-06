---
title: Il caricamento di convertire gli oggetti di Database in SQL Server (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-db2
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
ms.assetid: f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3
caps.latest.revision: "6"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a53fc54c474944739a839230ed9523aeeff9853c
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="loading-converted-database-objects-into-sql-server-db2tosql"></a>Il caricamento di convertire gli oggetti di Database in SQL Server (DB2ToSQL)
Dopo aver convertito schemi DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile caricare gli oggetti di database risultante in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile avere SSMA creare gli oggetti, oppure è possibile creare script degli oggetti ed eseguire gli script manualmente. SSMA consente inoltre di aggiornare i metadati di destinazione con il contenuto effettivo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Scelta tra sincronizzazione e gli script  
Se si desidera caricare gli oggetti di database convertito in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] senza alcuna modifica, si può avere SSMA direttamente a creare o ricreare gli oggetti di database. Tale metodo è rapido e semplice, ma non consentono la personalizzazione del [!INCLUDE[tsql](../../includes/tsql_md.md)] codice che definisce il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] gli oggetti, diversi dalle stored procedure.  
  
Se si desidera modificare il [!INCLUDE[tsql](../../includes/tsql_md.md)] utilizzato per creare oggetti o se si desidera maggiore controllo sulla creazione di oggetti, l'uso di SSMA per creare script. È possibile quindi modificare quegli script, creare individualmente ogni oggetto e anche utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent per pianificare la creazione di tali oggetti.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Utilizzo di SSMA per sincronizzare gli oggetti con SQL Server  
Utilizzo di SSMA per creare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] gli oggetti di database, si selezionano gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati e quindi sincronizzare gli oggetti con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], come illustrato nella procedura seguente. Per impostazione predefinita, se gli oggetti esistono già nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], e se i metadati SSMA sono più recenti rispetto all'oggetto in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], SSMA modificherà le definizioni degli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile modificare il comportamento predefinito modificando **impostazioni progetto**.  
  
> [!NOTE]  
> È possibile selezionare esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti che non sono stati convertiti dal database DB2 di database. Tuttavia, tali oggetti non verrà ricreati o modificati da SSMA.  
  
**Per sincronizzare gli oggetti con SQL Server**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, espandere inizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nodo, quindi espandere **database**.  
  
2.  Selezionare gli oggetti da elaborare:  
  
    -   Per sincronizzare un database completo, selezionare la casella di controllo accanto al nome del database.  
  
    -   Per sincronizzare o omettere i singoli oggetti o le categorie di oggetti, selezionare o deselezionare la casella di controllo accanto all'oggetto o una cartella.  
  
3.  Dopo aver selezionato gli oggetti da elaborare in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, fare doppio clic su **database**, quindi fare clic su **Sincronizza con Database**.  
  
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
  
2.  Nel **Salva con nome** finestra di dialogo, individuare la cartella in cui si desidera salvare lo script, immettere un nome di file nel **nome File** casella, quindi [!INCLUDE[clickOK](../../includes/clickok_md.md)]. SSMA aggiungerà l'estensione del nome file con estensione SQL.  
  
### <a name="modifying-scripts"></a>Modifica di script  
Dopo aver salvato il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] definizioni di oggetto come uno o più script, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] per visualizzare e modificare gli script.  
  
**Per modificare uno script**  
  
1.  Nel [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **File** dal menu **aprire**, quindi fare clic su **File**.  
  
2.  Nel **aprire** la finestra di dialogo, selezionare il file di script e quindi fare clic su OK.
  
3.  Modificare il file di script tramite l'editor di query.  
  
    Per ulteriori informazioni sull'editor di query, vedere "Editor comandi e funzionalità comode" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
4.  Per salvare lo script, fare clic su menu File **salvare**.  
  
### <a name="running-scripts"></a>Esecuzione di script  
È possibile eseguire in uno script o singole istruzioni, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Per eseguire uno script**  
  
1.  Nel [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **File** dal menu **aprire**, quindi fare clic su **File**.  
  
2.  Nel **aprire** finestra di dialogo, selezionare il file di script, quindi[!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
3.  Per eseguire lo script completo, premere il **F5** chiave.  
  
4.  Per eseguire un set di istruzioni, selezionare le istruzioni nella finestra dell'editor di query e quindi premere il **F5** chiave.  
  
Per ulteriori informazioni su come usare l'editor di query per eseguire gli script, vedere "[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)] Query" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
È inoltre possibile eseguire script dalla riga di comando utilizzando il **sqlcmd** utilità e dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] agente. Per ulteriori informazioni su **sqlcmd**, vedere la sezione "utilità sqlcmd" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, vedere "automatizzare le attività amministrative ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] agente)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="securing-objects-in-sql-server"></a>Protezione degli oggetti in SQL Server  
Dopo aver caricato gli oggetti di database convertito in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile concedere e negare autorizzazioni per tali oggetti. È consigliabile eseguire questa operazione prima della migrazione di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per informazioni su come proteggere gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere "Protezione considerazioni per i database e applicazioni di Database" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione consiste nel [la migrazione di dati DB2 in SQL Server](http://msdn.microsoft.com/en-us/86cbd39f-6dac-409a-9ce1-7dd54403f84b).  
  
## <a name="see-also"></a>Vedere anche  
[La migrazione dei dati di DB2 in SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
  
