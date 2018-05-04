---
title: Connessione a SQL Server (MySQLToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- connecting to SQL Server 2008, SQL Server permission
- connecting to SQL Server 2008, synchronization
ms.assetid: 08233267-693e-46e6-9ca3-3a3dfd3d2be7
caps.latest.revision: 18
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9f3b5b835f6fa5db7f88accacf041b8079ca954b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-sql-server-mysqltosql"></a>Connessione a SQL Server (MySQLToSQL)
Per eseguire la migrazione di database MySQL a SQL Server, è necessario connettersi all'istanza di destinazione di SQL Server. Quando ci si connette, SSMA Ottiene i metadati relativi a tutti i database nell'istanza di SQL Server e visualizza i metadati del database in Esplora i metadati di SQL Server. SSMA archivia le informazioni dell'istanza di SQL Server si è connessi a, ma non archivia le password.  
  
La connessione a SQL Server rimane attiva finché non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi a SQL Server se si desidera una connessione attiva al server. È possibile lavorare offline finché non si caricano gli oggetti di database SQL Server e la migrazione dei dati.  
  
I metadati sull'istanza di SQL Server non viene sincronizzato automaticamente. In alternativa, per aggiornare i metadati nel Visualizzatore metadati di SQL Server, è necessario aggiornare manualmente i metadati di SQL Server. Per ulteriori informazioni, vedere la sezione "La sincronizzazione di metadati di SQL Server" più avanti in questo argomento.  
  
## <a name="required-sql-server-permissions"></a>Autorizzazioni necessarie di SQL Server  
L'account utilizzato per connettersi a SQL Server richiede autorizzazioni diverse a seconda delle azioni eseguite l'account:  
  
-   Per convertire gli oggetti di MySQL per [!INCLUDE[tsql](../../includes/tsql_md.md)] sintassi, per aggiornare i metadati da SQL Server o per convertire la sintassi per salvare gli script, l'account deve disporre dell'autorizzazione per accedere all'istanza di SQL Server.  
  
-   Per caricare gli oggetti di database in SQL Server, i requisiti minimi di autorizzazione sono l'appartenenza di **db_owner** ruolo del database nel database di destinazione.  
  
## <a name="establishing-a-sql-server-connection"></a>Stabilire una connessione di SQL Server  
Prima di convertire gli oggetti di database MySQL in sintassi SQL Server, è necessario stabilire una connessione all'istanza di SQL Server in cui si desidera eseguire la migrazione i database MySQL.  
  
Quando si definiscono le proprietà di connessione, è inoltre possibile specificare il database in cui verranno migrati dati e oggetti. Dopo la connessione a SQL Server, è possibile personalizzare questo mapping al livello dello schema di MySQL. Per altre informazioni, vedere [Mapping database MySQL in schemi di SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> Prima di provare a connettersi a SQL Server, assicurarsi che l'istanza di SQL Server è in esecuzione e può accettare connessioni.  
  
**Per connettersi a SQL Server**  
  
1.  Nel **File** dal menu **Connetti al Server SQL** (dopo la creazione di un progetto, questa opzione è abilitata).  
  
    Se in precedenza, si è connessi a SQL Server, il nome di comando sarà **Riconnetti a SQL Server**.  
  
2.  Nella finestra di dialogo connessione, immettere o selezionare il nome dell'istanza di SQL Server.  
  
    -   Se ci si connette all'istanza predefinita nel computer locale, è possibile immettere **localhost** o un punto (**.**).  
  
    -   Se ci si connette all'istanza predefinita in un altro computer, immettere il nome del computer.  
  
    -   Se ci si connette a un'istanza denominata in un altro computer, immettere il nome del computer seguito da una barra rovesciata e il nome dell'istanza, ad esempio MyServer\MyInstance.  
  
3.  Se l'istanza di SQL Server è configurato per accettare le connessioni su una porta non predefinito, immettere il numero di porta utilizzato per le connessioni di SQL Server nel **porta Server** casella. Per l'istanza predefinita di SQL Server, il numero di porta predefinito è 1433. Per le istanze denominate, SSMA si tenterà di ottenere il numero di porta del servizio di SQL Server Browser.  
  
4.  Nel **autenticazione** , selezionare il tipo di autenticazione da utilizzare per la connessione. Per utilizzare l'account di Windows, selezionare **l'autenticazione di Windows**. Per utilizzare un account di accesso di SQL Server, selezionare autenticazione di SQL Server e quindi specificare il nome di accesso e password.  
  
5.  Per la connessione sicura, vengono aggiunti due controlli, la **Encrypt Connection** e **TrustServerCertificate** caselle di controllo. Solo quando **Encrypt Connection** è selezionata, il **TrustServerCertificate** casella di controllo è visibile. Quando **Encrypt Connection** è selezionata (true) e **TrustServerCertificate** non è selezionata (false), convaliderà il certificato SSL di SQL Server. La convalida del certificato del server fa parte dell'handshake SSL e assicura che il server a cui si esegue la connessione sia quello corretto. A tale scopo, deve essere installato un certificato sul lato client e sul lato server.  
  
6.  Fare clic su Connetti.  
  
**Compatibilità di versione superiore**  
  
È possibile connettersi o riconnettersi a versioni successive di SQL Server.  
  
1.  Sarà in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto creato è [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
2.  Sarà in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto creato è [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 ma non è consentito connettersi, ovvero le versioni precedenti [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005.  
  
3.  Sarà in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto creato è [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012.  
  
4.  Sarà possibile connettersi solo a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014 o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016 quando il progetto creato è [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014.  
  
5.  Compatibilità di versione superiore non è valida per "SQL Azure".  
  
||||||||  
|-|-|-|-|-|-|-|  
|**TIPO Visual Studio versione SERVER di destinazione del progetto**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005<br /> (Versione: 9)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008<br /> (Versione: 10. x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012<br />(Version:11.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014<br />(Version:12.x)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016<br />(Version:13.x)|SQL Azure|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005|Sì|Sì|Sì|Sì|Sì||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008||Sì|Sì|Sì|Sì||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012|||Sì|Sì|Sì||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2014||||Sì|Sì||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]2016|||||Sì||  
|SQL Azure||||||Sì|  
  
> [!IMPORTANT]  
> Conversione degli oggetti di database viene eseguita in base al tipo di progetto ma non per la versione del [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] connessi. In caso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] progetto 2005, la conversione viene eseguita in base [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005 anche se si è connessi a una versione successiva di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] (SQL Server 2008/SQL Server 2012 o SQL Server 2014/SQL Server 2016).  
  
## <a name="synchronizing-sql-server-metadata"></a>Sincronizzazione dei metadati SQL Server  
I metadati relativi a database di SQL Server non viene aggiornato automaticamente. I metadati nel Visualizzatore metadati di SQL Server sono uno snapshot dei metadati quando è connessa a SQL Server o l'ultima volta che si manualmente i metadati aggiornati. È possibile aggiornare manualmente i metadati per tutti i database o per qualsiasi singolo database o di un oggetto di database.  
  
**Per sincronizzare i metadati**  
  
1.  Assicurarsi di essere connessi a SQL Server.  
  
2.  In Esplora i metadati di SQL Server, selezionare la casella di controllo accanto al database o schema di database che si desidera aggiornare.  
  
    Ad esempio, per aggiornare i metadati per tutti i database, selezionare la casella accanto al database.  
  
3.  I database, o i singoli database o lo schema del database e quindi scegliere **Sincronizza con Database**.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping tra gli schemi di MySQL e SQL Server database e schemi, vedere [database MySQL di Mapping per gli schemi di SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   Per personalizzare le opzioni di configurazione per i progetti, vedere [impostazione delle opzioni di progetto &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere [tipi di dati di SQL Server e MySQL Mapping &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   Se non è necessario eseguire una di queste attività, è possibile convertire le definizioni degli oggetti di database MySQL in definizioni di oggetti di SQL Server. Per altre informazioni, vedere [conversione database MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Database MySQL la migrazione a SQL Server - SQL di Azure DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
