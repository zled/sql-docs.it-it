---
title: La connessione al database SQL di Azure (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d58bec0fb17e1661ba382dc3da04de04fb98f6f6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-azure-sql-db-sybasetosql"></a>La connessione al database SQL di Azure (SybaseToSQL)
Per eseguire la migrazione dei database Sybase a database SQL di Azure, è necessario connettersi all'istanza di destinazione del database SQL di Azure. Quando ci si connette, SSMA Ottiene i metadati relativi a tutti i database nell'istanza di database SQL di Azure e visualizza i metadati del database in Esplora i metadati di database di SQL Azure. SSMA archivia le informazioni dell'istanza di database SQL di Azure si è connessi a, ma non archivia le password.  
  
La connessione al database SQL di Azure rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi al database SQL di Azure se si desidera una connessione attiva al server. È possibile lavorare offline finché non si caricherà gli oggetti di database nel database SQL di Azure e la migrazione dei dati.  
  
I metadati sull'istanza di database SQL di Azure non viene sincronizzato automaticamente. In alternativa, per aggiornare i metadati nel Visualizzatore metadati di database SQL Azure, è necessario aggiornare manualmente i metadati di database SQL di Azure. Per ulteriori informazioni, vedere la sezione "La sincronizzazione di metadati di database SQL di Azure" più avanti in questo argomento.  
  
## <a name="required-azure-sql-db-permissions"></a>Le autorizzazioni di database SQL di Azure necessarie  
L'account utilizzato per connettersi al database SQL di Azure richiede autorizzazioni diverse a seconda delle azioni eseguite l'account:  
  
1.  Per convertire gli oggetti di Sybase a [!INCLUDE[tsql](../../includes/tsql_md.md)] sintassi, per aggiornare i metadati dal database SQL di Azure o per convertire la sintassi per salvare gli script, l'account deve disporre dell'autorizzazione per accedere all'istanza di database SQL di Azure.  
  
2.  Per caricare gli oggetti di database nel database SQL di Azure, il requisito di autorizzazione minima è l'appartenenza di **db_owner** ruolo del database nel database di destinazione.  
  
## <a name="establishing-a-azure-sql-db-connection"></a>Stabilire una connessione di database SQL di Azure  
Prima di convertire gli oggetti di database di Sybase alla sintassi del database SQL di Azure, è necessario stabilire una connessione all'istanza di database SQL di Azure in cui si desidera eseguire la migrazione i database di Sybase.  
  
Quando si definiscono le proprietà di connessione, è inoltre possibile specificare il database in cui verranno migrati dati e oggetti. Dopo la connessione al database SQL di Azure, è possibile personalizzare questo mapping al livello dello schema di Sybase. Per altre informazioni, vedere [Mapping Sybase ASE schemi di SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
> [!WARNING]  
> Prima di provare a connettersi al database SQL di Azure, assicurarsi che l'istanza di database SQL di Azure è in esecuzione e può accettare connessioni.  
  
**Per connettersi al database SQL di Azure**  
  
1.  Nel **File** dal menu **Connetti al database SQL di Azure**(dopo la creazione di un progetto, questa opzione è abilitata).  
  
    Se è già connessi al database SQL di Azure, il nome del comando sarà **riconnessione al database SQL di Azure**  
  
2.  Nella finestra di dialogo connessione, immettere o selezionare il nome del server di database SQL di Azure.  
  
3.  Immettere, selezionare o **Sfoglia** il nome del Database.  
  
4.  Immettere o selezionare **UserName**.  
  
5.  Immettere il **Password**.  
  
6.  SSMA consiglia una connessione crittografata al database SQL di Azure.  
  
7.  Fare clic su **Connetti**.  
  
> [!IMPORTANT]  
> SSMA per Sybase non supporta la connessione a **master** database nel database di SQL Azure.  
  
## <a name="synchronizing-azure-sql-db-metadata"></a>Sincronizzazione dei metadati di database SQL di Azure  
I metadati relativi a database di SQL Azure database non viene aggiornato automaticamente. I metadati nel Visualizzatore metadati di database SQL Azure sono uno snapshot dei metadati quando si è connessa al database SQL di Azure o l'ora dell'ultima aggiornare manualmente i metadati. È possibile aggiornare manualmente i metadati per tutti i database o per qualsiasi singolo database o di un oggetto di database.  
  
**Per sincronizzare i metadati**  
  
1.  Assicurarsi di essere connessi al database SQL di Azure.  
  
2.  Nel Visualizzatore metadati di database SQL di Azure, selezionare la casella di controllo accanto al database o schema di database che si desidera aggiornare.  
  
    Ad esempio, per aggiornare i metadati per tutti i database, selezionare la casella accanto al database.  
  
3.  I database, o i singoli database o lo schema del database e quindi scegliere **Sincronizza con Database**.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping tra schemi Sybase e il database di SQL Azure database e schemi, vedere [Mapping Sybase ASE schemi di SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
-   Per personalizzare le opzioni di configurazione per i progetti, vedere [impostazione delle opzioni di progetto &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere [Mapping Sybase ASE e tipi di dati di SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)  
  
-   Se non è necessario eseguire una di queste attività, è possibile convertire le definizioni degli oggetti di database Sybase in definizioni di oggetti di database SQL di Azure. Per altre informazioni, vedere [convertire gli oggetti di Database di Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Sybase ASE a SQL Server: SQL Azure database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
