---
title: Il caricamento di convertire gli oggetti di Database in SQL Server (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
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
helpviewer_keywords:
- Access databases, loading converted objects into SQL Azure
- Access databases, loading converted objects into SQL Server
- data, securing
- loading objects into SQL Azure
- loading objects into SQL Server
- migrating objects into SQL Azure
- migrating objects into SQL Server
- moving objects into SQL Azure
- moving objects into SQL Server
- schemas, loading into SQL Azure
- schemas, loading into SQL Server
- scripting converted objects
- securing data
- SQL Azure, loading objects into
- SQL Server, loading objects into
- synchronizing metadata with SQL Azure
- synchronizing metadata with SQL Server
- uploading objects into SQL Azure
- uploading objects into SQL Server
ms.assetid: 4e854eee-b10c-4f0b-9d9e-d92416e6f2ba
caps.latest.revision: "16"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 84bcfa558b42cc272e314f40948ee3bc86e7ef2b
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="loading-converted-database-objects-into-sql-server-accesstosql"></a>Il caricamento di convertire gli oggetti di Database in SQL Server (AccessToSQL)
Dopo aver convertito oggetti di database di Access da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, è possibile caricare gli oggetti di database risultante in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È possibile avere SSMA creare gli oggetti, oppure è possibile creare script degli oggetti ed eseguire gli script manualmente. SSMA consente inoltre di aggiornare i metadati di destinazione con il contenuto effettivo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o database di SQL Azure.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Scelta tra sincronizzazione e gli script  
Se si desidera caricare gli oggetti di database convertito in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure senza modifiche, è possibile avere SSMA direttamente a creare o ricreare gli oggetti di database. Tale metodo è rapido e semplice, ma non consentono la personalizzazione del [!INCLUDE[tsql](../../includes/tsql_md.md)] codice che definisce il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di SQL Azure, diversi dalle stored procedure.  
  
Se si desidera modificare il [!INCLUDE[tsql](../../includes/tsql_md.md)] utilizzato per creare oggetti o se si desidera maggiore controllo sulla creazione di oggetti, l'uso di SSMA per creare script. È possibile quindi modificare quegli script, creare individualmente ogni oggetto e anche utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent per pianificare la creazione di tali oggetti.  
  
## <a name="using-ssma-to-synchronize-objects-with-sql-server"></a>Utilizzo di SSMA per sincronizzare gli oggetti con SQL Server  
Utilizzare SSMA per creare [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o oggetti di database SQL Azure, si selezionano gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure e quindi sincronizzare gli oggetti con [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure, come illustrato nella procedura seguente. Per impostazione predefinita, se gli oggetti esistono già nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure e se i metadati SSMA alcune modifiche locali o gli aggiornamenti alla definizione di tali oggetti molto, allora SSMA modificherà le definizioni degli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È possibile modificare il comportamento predefinito modificando **impostazioni progetto**.  
  
> [!NOTE]  
> È possibile selezionare esistente [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o gli oggetti di database SQL Azure non sono stati convertiti dal database di Access. SSMA verrà, tuttavia, non ricreare o modificare tali oggetti.  
  
**Per sincronizzare gli oggetti con SQL Server o SQL Azure**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati di SQL Azure, espandere la parte superiore o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o nodo di SQL Azure, quindi espandere **database**.  
  
2.  Selezionare gli oggetti da elaborare:  
  
    -   Per sincronizzare un database completo, selezionare la casella di controllo accanto al nome del database.  
  
    -   Per sincronizzare o omettere i singoli oggetti o le categorie di oggetti, selezionare o deselezionare la casella di controllo accanto all'oggetto o una cartella.  
  
3.  Dopo aver selezionato gli oggetti da elaborare in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o Visualizzatore metadati di SQL Azure, fare doppio clic su **database**, quindi fare clic su **Sincronizza con Database**.  
  
    È inoltre possibile sincronizzare oggetti singoli o le categorie di oggetti facendo clic l'oggetto o la relativa cartella padre, e quindi fare clic su **Sincronizza con Database**.  
  
    Successivamente, verrà visualizzato SSMA il **Sincronizza con Database** finestra di dialogo, in cui è possibile visualizzare due gruppi di elementi. Sul lato sinistro, SSMA viene rappresentati in un albero di oggetti di database selezionati. Sul lato destro, è possibile visualizzare una struttura ad albero che rappresentano gli stessi oggetti di metadati SSMA. È possibile espandere l'albero facendo clic sulla destra o sinistra pulsante ' +'. La direzione della sincronizzazione è visualizzata nella colonna azione inserita tra i due alberi.  
  
    Un segno di azione può trovarsi in tre stati:  
  
    -   Una freccia a sinistra, significa che verrà salvato il contenuto dei metadati del database (predefinito).  
  
    -   Una freccia a destra significa che il contenuto di database sovrascriverà i metadati SSMA.  
  
    -   Una croce, significa che verrà intrapresa alcuna azione.  
  
    Fare clic sul segno di azione di modifica dello stato. Sincronizzazione effettiva verrà eseguita quando si fa clic **OK** pulsante il **Sincronizza con Database** finestra di dialogo.  
  
## <a name="scripting-objects"></a>Oggetti di scripting  
Se si desidera salvare [!INCLUDE[tsql](../../includes/tsql_md.md)] definizioni di oggetti di database convertito, o si desidera modificare le definizioni degli oggetti e generare script per eseguire manualmente, è possibile salvare le definizioni degli oggetti per il database convertito [!INCLUDE[tsql](../../includes/tsql_md.md)] script.  
  
**Per salvare uno o più oggetti in uno script**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, espandere il nodo principale (il nome del server) e quindi **database**.  
  
2.  Eseguire una o più delle operazioni seguenti:  
  
    -   Per creare lo script di un database completo, selezionare la casella di controllo accanto al nome del database.  
  
    -   Per creare uno script o omettere singole visualizzazioni, espandere il database, **viste**e quindi selezionare o deselezionare la casella di controllo accanto a vista.  
  
    -   Per creare uno script o omettere le singole tabelle, espandere il database, **tabelle**e quindi selezionare o deselezionare la casella di controllo accanto alla tabella.  
  
    -   Per creare uno script o omettere singoli indici per una tabella, espandere la tabella, **indici**e quindi selezionare o deselezionare l'indice.  
  
3.  Fare doppio clic su **database** e selezionare **salvare come Script**.  
  
    È inoltre possibile generare script singoli oggetti. Per creare lo script di un oggetto, indipendentemente da quali oggetti sono selezionati, l'oggetto e scegliere **salvare come Script**.  
  
4.  Nel **Salva con nome** finestra di dialogo, individuare la cartella in cui si desidera salvare lo script, immettere un nome di file nel **nome File** casella e quindi fare clic su **OK**.  
  
    SSMA aggiungerà l'estensione del nome file con estensione SQL.  
  
### <a name="modifying-scripts"></a>Modifica di script  
Dopo aver salvato il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o definizioni di oggetti di SQL Azure come uno script, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] per modificare lo script.  
  
**Per modificare uno script**  
  
1.  Nel [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] **File** dal menu **aprire**, quindi fare clic su **File**.  
  
2.  Nel **aprire** nella finestra di dialogo individuare e selezionare il file di script e quindi fare clic su **OK**.  
  
3.  Modificare il file di script tramite l'editor di query.  
  
    Per ulteriori informazioni sull'editor di query, vedere "Editor comandi e funzionalità comode" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
4.  Per salvare lo script, dal menu File, selezionare **salvare**.  
  
### <a name="running-scripts"></a>Esecuzione di script  
È possibile eseguire in uno script o singole istruzioni, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Per eseguire uno script**  
  
1.  Nel [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] **File** dal menu **aprire** e quindi fare clic su **File**.  
  
2.  Nel **aprire** nella finestra di dialogo individuare e selezionare il file di script e quindi fare clic su **OK**.  
  
3.  Per eseguire lo script completo, premere il **F5** chiave.  
  
4.  Per eseguire un set di istruzioni, selezionare le istruzioni nella finestra dell'editor di query e quindi premere il **F5** chiave.  
  
Per ulteriori informazioni su come usare l'editor di query per eseguire gli script, vedere "[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] [!INCLUDE[tsql](../../includes/tsql_md.md)] Query" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
È inoltre possibile eseguire script dalla riga di comando utilizzando il **sqlcmd** utilità e da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] agente. Per ulteriori informazioni su **sqlcmd**, vedere la sezione "utilità sqlcmd" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, vedere "automatizzare le attività amministrative ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] agente)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="securing-objects-in-sql-server"></a>Protezione degli oggetti in SQL Server  
Dopo aver caricato gli oggetti di database convertito in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile concedere e negare autorizzazioni per tali oggetti. È consigliabile eseguire questa operazione prima della migrazione di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per informazioni su come proteggere gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vedere "Protezione considerazioni per i database e applicazioni di Database" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] documentazione in linea.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione è [la migrazione dei dati in SQL Server](http://msdn.microsoft.com/en-us/f3b18af7-1af0-499d-a00d-a0af94895625).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
