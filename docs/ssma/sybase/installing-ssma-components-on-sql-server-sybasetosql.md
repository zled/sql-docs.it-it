---
title: Installazione dei componenti SSMA in SQL Server (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 5ad9e12c-2cdb-4dd2-8703-05a23242d19d
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 716a45f706292e3011ed5c8c2871bfc8176fb5a5
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="installing-ssma-components-on-sql-server-sybasetosql"></a>Installazione dei componenti SSMA in SQL Server (SybaseToSQL)
Oltre a installare SSMA per l'utilizzo di migrazione dei dati lato Server, è necessario installare anche i componenti nel computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Questi componenti includono il Service pack estensione SSMA, che supporta la migrazione dei dati e provider Sybase per abilitare la connettività di server a server.  
  
## <a name="ssma-for-sybase-extension-pack"></a>SSMA per Sybase estensione Pack  
Il pacchetto di estensione SSMA aggiunge i database, **sysdb** e **ssmatesterdb_syb**, per l'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Il **sysdb** database contiene tabelle e stored procedure necessarie per la migrazione dei dati. Il **ssmatester_syb** database contiene lo schema **ssma_sybase_utilities**, in cui vengono creati gli oggetti (tabelle, trigger, viste) utilizzati dal componente tester SSMA.  
  
Inoltre, quando si esegue la migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], crea SSMA [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] agente dei processi quando il modulo di migrazione dei dati lato server viene utilizzato per la migrazione dei dati.  
  
### <a name="installing-the-extension-pack"></a>Installare il pacchetto di estensione  
È possibile installare qualsiasi momento prima di migrare i dati per il pacchetto di estensione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
> [!IMPORTANT]  
> Per installare il pacchetto di estensione, è necessario essere un membro del ruolo del server sysadmin nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
**Per installare il pacchetto di estensione**  
  
1.  Copiare SSMA per Sybase estensione Pack. *n*. Install.exe, in cui  *n*  è il numero di build, al computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
2.  Fare doppio clic su SSMA per Sybase estensione Pack. *n*. Install.exe.  
  
3.  Nella pagina di benvenuto fare clic su **Avanti**.  
  
4.  Nella pagina Contratto di licenza leggere il contratto di licenza. Se si accetta, selezionare il **accetto i termini del contratto di licenza** casella di controllo e quindi fare clic su **Avanti**.  
  
5.  Nella pagina Selezione tipo di installazione, fare clic su **tipica**.  
  
6.  Scegliere la pagina Inizio installazione, **installare**.  
  
7.  Nella pagina Installazione del primo passaggio di completato, fare clic su **Avanti**.  
  
    Verrà visualizzata una nuova finestra di dialogo, in cui si seleziona l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] per l'installazione di Service pack di estensione.  
  
8.  Selezionare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui verrà migrazione database ASE e quindi fare clic su **Avanti**.  
  
    L'istanza predefinita è lo stesso nome del computer. Le istanze denominate saranno seguite da una barra rovesciata e il nome dell'istanza.  
  
9. Nella pagina parametri di connessione, selezionare il metodo di autenticazione e quindi fare clic su **Avanti**.  
  
    L'autenticazione di Windows utilizzerà le credenziali di Windows per tentare di accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Se si seleziona [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] l'autenticazione, è necessario immettere un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nome account di accesso e password.  
  
10. Nella pagina Amministrazione Server, selezionare **installare Database utilità**  *n* , dove  *n*  è il numero di versione e quindi fare clic su **Avanti**.  
  
    Il **sysdb** database viene creato e le stored procedure vengono create in tale database.  
  
    Se **installare Database Tester** opzione è selezionata il tester **ssmatesterdb_syb** database verrà creato.  
  
11. Per installare le utilità in un'altra istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]selezionare **tornare alle istanze**, quindi fare clic su **successivo**. Per uscire dalla procedura guidata, fare clic su **uscire**.  
  
### <a name="sql-server-database-objects"></a>Oggetti di Database SQL Server  
Dopo aver installato il pacchetto di estensione, sarà possibile vedere un **ssma_syb.bcp_migration_packages** tabella il **sysdb** database. Si verifica anche le stored procedure seguenti:  
  
-   **bcp_clean_migration_data**  
  
-   **bcp_ensure_message_table**  
  
-   **bcp_insert_new_message**  
  
-   **bcp_post_process**  
  
-   **bcp_read_new_migration_messages**  
  
-   **bcp_save_migration_package**  
  
-   **bcp_smart_truncate**  
  
-   **bcp_start_migration_process**  
  
-   **get_jobstep_info**  
  
-   **stop_agent_process**  
  
Ogni volta che si esegue la migrazione di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], SSMA crea un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] processo dell'agente. Questi processi sono denominati **pacchetto di migrazione di dati ssma_syb {GUID}**e sono visibili nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] nodo agenti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] nella cartella processi.  
  
## <a name="sybase-providers"></a>Provider di Sybase  
Quando si esegue la migrazione dati da ASE a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]esegue la migrazione dei dati di SQL Azure, direttamente tra ASE e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure. Non è passa attraverso SSMA a perché ciò potrebbe rallentare la migrazione dei dati.  
  
### <a name="installing-the-sybase-providers"></a>Installare i provider di Sybase  
Le istruzioni seguenti illustrano i passaggi di installazione di base per l'installazione di provider di Sybase. Le istruzioni esatte variano a seconda della versione del programma di installazione di Sybase.  
  
> [!IMPORTANT]  
> Prima di eseguire il programma di installazione, verificare di non violare i contratti di licenza.  
  
1.  Eseguire il programma di installazione di Sybase ASE.  
  
2.  Selezionare il programma di installazione personalizzato.  
  
3.  Nella pagina Selezione funzionalità selezionare i provider di dati ODBC, OLE DB e ADO.NET.  
  
4.  Verificare le funzionalità selezionate e quindi fare clic su **fine** per installare il provider di dati.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per Sybase Client &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Migrazione di database di Sybase ASE a SQL Server: database SQL di Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

