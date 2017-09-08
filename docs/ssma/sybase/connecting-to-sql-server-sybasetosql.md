---
title: Connessione a SQL Server (SybaseToSQL) | Documenti Microsoft
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
helpviewer_keywords:
- Connecting to SQL Server
ms.assetid: dd368a1a-45b0-40e9-b4d3-5cdb48c26606
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3dd8b595d897aad93d580447af4afed330cb71f9
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="connecting-to-sql-server-sybasetosql"></a>Connessione a SQL Server (SybaseToSQL)
Per eseguire la migrazione dei database Sybase Adaptive Server Enterprise (ASE) [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è necessario connettersi a qualsiasi istanza di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Quando ci si connette, SSMA Ottiene i metadati relativi a tutti i database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e visualizza i metadati del database nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati. SSMA archivia le informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] si è connessi a, ma non archivia le password.  
  
La connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se si desidera una connessione attiva al server. È possibile lavorare offline solo dopo aver caricato gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati.  
  
I metadati sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non viene sincronizzato automaticamente. In alternativa, se si desidera aggiornare i metadati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, è necessario aggiornare manualmente il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadati, come descritto nel "Synchronizing [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadati" sezione più avanti in questo argomento.  
  
## <a name="required-sql-server-permissions"></a>Autorizzazioni necessarie di SQL Server  
L'account utilizzato per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] richiede autorizzazioni diverse a seconda delle azioni eseguite da quell'account.  
  
-   Per convertire gli oggetti di base per [!INCLUDE[tsql](../../includes/tsql_md.md)] sintassi, per aggiornare i metadati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], o per salvare gli script convertita sintassi, l'account deve disporre dell'autorizzazione per accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Per caricare gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], i requisiti minimi di autorizzazione sono l'appartenenza di **db_owner** ruolo del database nel database di destinazione.  
  
-   La migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], l'account deve essere un membro del **sysadmin** ruolo del server. Questa operazione è necessaria per eseguire il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] pacchetti la migrazione dei dati dell'agente.  
  
-   Per eseguire il codice generato da SSMA, l'account deve disporre **Execute** le autorizzazioni per tutte le funzioni definite dall'utente nel **ssma_syb** dello schema del **sysdb** database. Queste funzioni forniscono una funzionalità equivalente ASE delle funzioni di sistema e vengono utilizzate per gli oggetti convertiti.  
  
Se l'account utilizzato per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è per eseguire la migrazione di tutte le attività, l'account deve essere un membro del **sysadmin** ruolo del server.  
  
## <a name="establishing-a-sql-server-connection"></a>Stabilire una connessione di SQL Server  
Prima di convertire oggetti di database ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, è necessario stabilire una connessione all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui si desidera eseguire la migrazione di database di base o dei database.  
  
Quando si definiscono le proprietà di connessione, è inoltre possibile specificare il database in cui verranno migrati dati e oggetti. È possibile personalizzare il mapping a livello di schema ASE dopo la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni, vedere [Mapping Sybase ASE schemi per gli schemi di SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
> [!IMPORTANT]  
> Prima di provare a connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], assicurarsi che l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è in esecuzione e può accettare connessioni.  
  
**Per connettersi a SQL Server**  
  
1.  Nel **File** dal menu **Connetti al Server SQL**.  
  
    Se si è connessi in precedenza per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], il nome di comando sarà **Riconnetti a SQL Server**.  
  
2.  Nella finestra di dialogo connessione, immettere o selezionare il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Se ci si connette all'istanza predefinita nel computer locale, è possibile immettere **localhost** o un punto (**.**).  
  
    -   Se ci si connette all'istanza predefinita in un altro computer, immettere il nome del computer.  
  
    -   Se ci si connette a un'istanza denominata in un altro computer, immettere il nome del computer seguito da una barra rovesciata e il nome dell'istanza, ad esempio MyServer\MyInstance.  
  
3.  Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è configurato per accettare le connessioni su una porta non predefinito, immettere il numero di porta utilizzato per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] connessioni nel **porta Server** casella. Per l'istanza predefinita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], il numero di porta predefinito è 1433. Per le istanze denominate, SSMA tenterà di ottenere il numero di porta di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] servizio Browser.  
  
4.  Nel **Database** , immettere il nome del database di destinazione.  
  
    Questa opzione non è disponibile durante la riconnessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
5.  Nel **autenticazione** , selezionare il tipo di autenticazione da utilizzare per la connessione. Per utilizzare l'account di Windows, selezionare **l'autenticazione di Windows**. Per utilizzare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] account di accesso, selezionare **autenticazione di SQL Server** e quindi specificare il nome di account di accesso e password.  
  
6.  Per la connessione sicura, vengono aggiunti due controlli, la **Encrypt Connection** e **TrustServerCertificate** caselle di controllo. Solo quando **Encrypt Connection** è selezionata, il **TrustServerCertificate** casella di controllo è visibile. Quando **Encrypt Connection** è selezionata (true) e **TrustServerCertificate** non è selezionata (false), convaliderà il certificato SSL di SQL Server. La convalida del certificato del server fa parte dell'handshake SSL e assicura che il server a cui si esegue la connessione sia quello corretto. A tale scopo, deve essere installato un certificato sul lato client e sul lato server.  
  
7.  Fare clic su **Connetti**.  
  
**Compatibilità di versione superiore**  
  
-   Sarà in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto di migrazione creato è [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   Sarà in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto di migrazione creato è [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 ma non sarà in grado di connettersi a versioni precedenti, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   Sarà possibile connettersi solo a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto creato è SQL Server 2012.  
  
-   Compatibilità di versione superiore non è valida per SQL Azure.  
  
||||||||
|-|-|-|-|-|-|-|
|**VERSIONE SERVER di destinazione e tipo di progetto**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005<br /> (Versione: 9)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008<br /> (Versione: 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 <br />(Version:13.x)|SQL Azure|
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|Sì|Sì|Sì|Sì|Sì||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||Sì|Sì|Sì|Sì||
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||Sì|Sì|Sì||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014||||Sì|Sì|| 
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016|||||Sì||  
|SQL Azure||||||Sì|  
  
> [!IMPORTANT]  
> Conversione degli oggetti di database viene eseguita in base al tipo di progetto ma non per la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] si è connessi. In caso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] progetto 2005, la conversione viene eseguita in base [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 anche se si è connessi a una versione successiva di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016)  
  
## <a name="reconnecting-to-sql-server"></a>Connettersi a SQL Server  
La connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se si desidera una connessione attiva al server. È possibile lavorare offline finché non si aggiorna i metadati, oggetti di database di carico in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], e la migrazione dei dati.  
  
La procedura per la riconnessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è uguale a quella per stabilire una connessione.  
  
## <a name="synchronizing-sql-server-metadata"></a>Sincronizzazione dei metadati SQL Server  
I metadati relativi al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database non viene aggiornato automaticamente. I metadati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati è uno snapshot dei metadati quando si è connessi prima di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], o l'ultima volta che si metadati aggiornati manualmente. È possibile aggiornare manualmente i metadati per tutti i database o per qualsiasi singolo database o di un oggetto di database.  
  
**Per sincronizzare i metadati**  
  
1.  Assicurarsi che si è connessi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
2.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, selezionare la casella di controllo accanto al database o database dello schema che si desidera aggiornare.  
  
    Ad esempio, per aggiornare i metadati per tutti i database, selezionare la casella accanto a **database**.  
  
3.  Database o i singoli database o lo schema del database e quindi scegliere **Sincronizza con Database**.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Se si desidera personalizzare il mapping tra i database di base e gli schemi e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database e schemi, vedere [gli schemi di Mapping Sybase ASE per gli schemi di SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md).  
  
-   Se si desidera personalizzare le opzioni di configurazione per i progetti, vedere [impostazione delle opzioni progetto &#40; SybaseToSQL &#41; ](../../ssma/sybase/setting-project-options-sybasetosql.md).  
  
-   Se si desidera personalizzato per il mapping dei tipi di dati di origine e di destinazione, vedere [Mapping Sybase ASE e tipi di dati di SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
-   Se non è necessario effettuare una delle seguenti, è possibile convertire le definizioni degli oggetti di database di Sybase ASE in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] definizioni di oggetti. Per ulteriori informazioni, vedere [convertire gli oggetti di Database di Sybase ASE &#40; SybaseToSQL &#41; ](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Sybase ASE a SQL Server: database SQL di Azure &#40; SybaseToSQL &#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  

