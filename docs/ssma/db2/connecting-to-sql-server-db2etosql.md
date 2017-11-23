---
title: Connessione a SQL Server (DB2eToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: b59803cb-3cc6-41cc-8553-faf90851410e
caps.latest.revision: "8"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: de9a7af8f191f3c979075de204e4a887128b9c1d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="connecting-to-sql-server-db2etosql"></a>Connessione a SQL Server (DB2eToSQL)
Per eseguire la migrazione di database DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]database di SQL Server 2014 o Azure è necessario connettersi a uno qualsiasi di queste istanze di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Quando ci si connette, SSMA Ottiene i metadati relativi a tutti i database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e visualizza i metadati del database nel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati. SSMA archivia le informazioni sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] si è connessi a, ma non archivia le password.  
  
La connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se si desidera una connessione attiva al server. È possibile lavorare offline solo dopo aver caricato gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] e la migrazione dei dati.  
  
I metadati sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] non viene sincronizzato automaticamente. In alternativa, per aggiornare i metadati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, è necessario aggiornare manualmente il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dei metadati. Per ulteriori informazioni, vedere la "Synchronizing [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] metadati" più avanti in questo argomento.  
  
## <a name="required-sql-server-permissions"></a>Autorizzazioni necessarie di SQL Server  
L'account utilizzato per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] richiede autorizzazioni diverse a seconda delle azioni eseguite l'account:  
  
-   Per convertire gli oggetti di DB2 per [!INCLUDE[tsql](../../includes/tsql_md.md)] sintassi, per aggiornare i metadati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], o per salvare gli script convertita sintassi, l'account deve disporre dell'autorizzazione per accedere all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
-   Per caricare gli oggetti di database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], l'account deve essere un membro del **sysadmin** ruolo del server. Ciò è necessario installare gli assembly CLR.  
  
-   La migrazione dei dati per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], l'account deve essere un membro del **sysadmin** ruolo del server. Questa operazione è necessaria per eseguire il [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] pacchetti la migrazione dei dati dell'agente.  
  
-   Per eseguire il codice generato da SSMA, l'account deve disporre **Execute** le autorizzazioni per tutte le funzioni definite dall'utente nel **ssma_DB2** dello schema del database di destinazione. Queste funzioni forniscono una funzionalità equivalente delle funzioni di sistema DB2 e vengono utilizzate per gli oggetti convertiti.  
  
Se l'account utilizzato per connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] è per eseguire la migrazione di tutte le attività, l'account deve essere un membro del **sysadmin** ruolo del server.  
  
## <a name="establishing-a-sql-server-connection"></a>Stabilire una connessione di SQL Server  
Prima di convertire oggetti di database DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] sintassi, è necessario stabilire una connessione all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in cui si desidera eseguire la migrazione i database DB2.  
  
Quando si definiscono le proprietà di connessione, è inoltre possibile specificare il database in cui verranno migrati dati e oggetti. È possibile personalizzare il mapping a livello di schema DB2 dopo la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Per ulteriori informazioni, vedere [Mapping DB2 schemi DB2ToSQL gli schemi di SQL Server &#40; &#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
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
  
    Questa opzione non è disponibile quando si riconnette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
5.  Nel **autenticazione** , selezionare il tipo di autenticazione da utilizzare per la connessione. Per utilizzare l'account di Windows, selezionare **l'autenticazione di Windows**. Per utilizzare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] account di accesso, selezionare **autenticazione di SQL Server**, quindi specificare il nome di accesso e la password.  
  
6.  Per la connessione sicura, vengono aggiunti due controlli, la **Encrypt Connection** e **TrustServerCertificate** caselle di controllo. Solo quando **Encrypt Connection** è selezionata, il **TrustServerCertificate** casella di controllo è visibile. Quando **Encrypt Connection** è selezionata (true) e **TrustServerCertificate** non è selezionata (false), convaliderà il certificato SSL di SQL Server. La convalida del certificato del server fa parte dell'handshake SSL e assicura che il server a cui si esegue la connessione sia quello corretto. A tale scopo, deve essere installato un certificato sul lato client e sul lato server.  
  
7.  Fare clic su **Connetti**.  
  
**Compatibilità di versione superiore**  
  
-   Sarà in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto di migrazione creato è [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   Sarà in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto di migrazione creato è [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 ma non sarà in grado di connettersi a versioni precedenti, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
-   Sarà in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto creato è SQL Server 2012.  
  
||||||  
|-|-|-|-|-|  
|**VERSIONE SERVER di destinazione e tipo di progetto**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 <br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 <br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 <br />(Version:13.x)|Database SQL di Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|Sì|Sì|Sì||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014||Sì|Sì||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014|||Sì||  
|Database SQL di Azure||||Sì|  
  
> [!IMPORTANT]  
> Conversione degli oggetti di database viene eseguita in base al tipo di progetto ma non per la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] si è connessi. In caso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database di SQL Server 2016 o Azure.  
  
## <a name="synchronizing-sql-server-metadata"></a>Sincronizzazione dei metadati SQL Server  
I metadati relativi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database non viene aggiornato automaticamente. I metadati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati è uno snapshot dei metadati quando si è connessi prima di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], o l'ultima volta che si metadati aggiornati manualmente. È possibile aggiornare manualmente i metadati per tutti i database o per qualsiasi singolo database o di un oggetto di database.  
  
**Per sincronizzare i metadati**  
  
1.  Assicurarsi che si è connessi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
2.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Visualizzatore metadati, selezionare la casella di controllo accanto al database o database dello schema che si desidera aggiornare.  
  
    Ad esempio, per aggiornare i metadati per tutti i database, selezionare la casella accanto a **database**.  
  
3.  Fare doppio clic su **database**, o il singolo database o lo schema del database e quindi selezionare **Sincronizza con Database**.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping tra gli schemi di DB2 e [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] database e schemi, vedere [schemi DB2 di Mapping per gli schemi di SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/mapping-db2-schemas-to-sql-server-schemas-db2tosql.md).  
  
-   Per personalizzare le opzioni di configurazione per i progetti, vedere [impostazioni progetto &#40; Conversione &#41; &#40; DB2ToSQL &#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md) e le relative sezioni.  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere [DB2ToSQL Mapping DB2 e tipi di dati di SQL Server &#40; &#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md).  
  
-   Se non è necessario eseguire una di queste attività, è possibile convertire le definizioni degli oggetti di database di DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] definizioni di oggetti. Per ulteriori informazioni, vedere [DB2ToSQL la conversione di schemi di DB2 &#40; &#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database DB2 a SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
