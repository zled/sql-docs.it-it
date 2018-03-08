---
title: La connessione al database SQL di Azure (AccessToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
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
- instance of SQL Azure
- metadata, refreshing
- refreshing metadata
- SQL Azure
- SQL Azure, connecting
- SQL Azure, connecting to
- SQL Azure, reconnecting
- SQL Azure, synchronizing metadata
ms.assetid: 1ba0d113-dc05-4431-8689-e14a8821bafd
caps.latest.revision: "21"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e68c4b94210234875eebbe166f83d87baebbc0e1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-to-azure-sql-db-accesstosql"></a>La connessione al database SQL di Azure (AccessToSQL)
Per eseguire la migrazione di database di Access a SQL Azure, è necessario connettersi all'istanza di destinazione di SQL Azure. Quando ci si connette, SSMA Ottiene i metadati relativi a tutti i database nell'istanza di SQL Azure e visualizza i metadati del database in Esplora risorse di metadati di SQL Azure. SSMA archivia le informazioni sull'istanza di SQL Azure si è connessi a, ma non archivia le password.  
  
La connessione a SQL Azure rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi a SQL Azure se si desidera una connessione attiva al server. È possibile lavorare offline finché non si caricano gli oggetti di database SQL Azure e la migrazione dei dati.  
  
I metadati sull'istanza di SQL Azure non viene sincronizzato automaticamente. In alternativa, per aggiornare i metadati nel Visualizzatore metadati di SQL Azure, è necessario aggiornare manualmente i metadati di SQL Azure. Per ulteriori informazioni, vedere la sezione "La sincronizzazione di metadati di SQL Azure" più avanti in questo argomento.  
  
## <a name="required-sql-azure-permissions"></a>SQL necessarie autorizzazioni di Azure  
L'account utilizzato per connettersi a SQL Azure richiede autorizzazioni diverse a seconda delle azioni eseguite l'account:  
  
-   Per convertire oggetti di Access da [!INCLUDE[tsql](../../includes/tsql_md.md)] sintassi, per aggiornare i metadati da SQL Azure o per convertire la sintassi per salvare gli script, l'account deve disporre dell'autorizzazione per accedere all'istanza di SQL Azure.  
  
-   Per caricare gli oggetti di database in SQL Azure, il requisito di autorizzazione minima è l'appartenenza di **db_owner** ruolo del database nel database di destinazione.  
  
## <a name="establishing-a-sql-azure-connection"></a>La definizione di un database SQL Azure connessione  
Prima di convertire gli oggetti di database di Access in sintassi SQL Azure, è necessario stabilire una connessione all'istanza di SQL Azure in cui si desidera eseguire la migrazione del database o database.  
  
Quando si definiscono le proprietà di connessione, è inoltre possibile specificare il database in cui verranno migrati dati e oggetti. Dopo la connessione a SQL Azure, è possibile personalizzare questo mapping al livello dello schema di accesso. Per ulteriori informazioni, vedere [Mapping accesso database di SQL Server](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4)  
  
> [!IMPORTANT]  
> Prima di provare a connettersi a SQL Azure, assicurarsi che l'istanza di SQL Azure è in esecuzione e può accettare connessioni.  
  
**Per connettersi a SQL Azure**  
  
1.  Nel **File** dal menu **Connetti a SQL Azure** (dopo la creazione di un progetto, questa opzione è abilitata).  
  
    Se in precedenza connesso a SQL Azure, il nome di comando sarà **Riconnetti a SQL Azure**.  
  
2.  Nella finestra di dialogo connessione, immettere o selezionare il nome del server di SQL Azure.  
  
3.  Immettere, selezionare o **Sfoglia** il nome del Database.  
  
4.  Immettere o selezionare **UserName**.  
  
5.  Immettere il **Password**.  
  
6.  SSMA consiglia una connessione crittografata a SQL Azure.  
  
7.  Fare clic su **Connetti**.  
  
> [!IMPORTANT]  
> SSMA per l'accesso non supporta la connessione a **master** database in SQL Azure.  
  
Se non sono disponibili database nell'account di SQL Azure, è possibile creare il primo database utilizzando **Create Database Azure** opzione visualizzata fare clic su di **Sfoglia** pulsante.  
  
## <a name="synchronizing-sql-azure-metadata"></a>La sincronizzazione di SQL Azure metadati  
I metadati relativi a database di SQL Azure non viene aggiornato automaticamente. I metadati nel Visualizzatore metadati di SQL Azure sono uno snapshot dei metadati quando è connessa a SQL Azure o l'ultima volta che si manualmente i metadati aggiornati. È possibile aggiornare manualmente i metadati per tutti i database o per qualsiasi singolo database o di un oggetto di database.  
  
**Per sincronizzare i metadati**  
  
1.  Assicurarsi di essere connessi a SQL Azure.  
  
2.  Nel Visualizzatore metadati di SQL Azure, selezionare la casella di controllo accanto al database o schema di database che si desidera aggiornare.  
  
    Ad esempio, per aggiornare i metadati per tutti i database, selezionare la casella accanto al database.  
  
3.  I database, o i singoli database o lo schema del database e quindi scegliere **Sincronizza con Database**.  
  
## <a name="refreshing-sql-azure-metadata"></a>Aggiornamento di SQL Azure metadati  
Se gli schemi di SQL Azure modificano dopo la connessione, è possibile aggiornare i metadati del server.  
  
**Per aggiornare i metadati di SQL Azure**  
  
-   Nel Visualizzatore metadati di SQL Azure, fare clic **database**, quindi selezionare **aggiornamento dal Database**.  
  
## <a name="reconnecting-to-sql-azure"></a>Connettersi a SQL Azure  
La connessione a SQL Azure rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi a SQL Azure se si desidera una connessione attiva al server. È possibile lavorare offline finché non si caricano gli oggetti di database SQL Azure e la migrazione dei dati.  
  
La procedura per la connessione a SQL Azure è uguale a quella per stabilire una connessione.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping tra gli schemi di accesso e database di SQL Azure e schemi, vedere [Mapping accesso database di SQL Server](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4).  
  
-   Per personalizzare le opzioni di configurazione per i progetti, vedere [impostazione delle opzioni progetto](http://msdn.microsoft.com/en-us/0a7304df-2f35-4453-96ef-7ac83dea1167).  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere [Mapping tipi di origine e destinazione dati](http://msdn.microsoft.com/en-us/b362a075-16e7-423f-b63f-e1e9f02844a9).  
  
-   Se non è necessario eseguire una di queste attività, è possibile convertire le definizioni degli oggetti di database di Access in definizioni di oggetti di SQL Azure. Per ulteriori informazioni, vedere [la conversione dei database di Access](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
