---
title: "Gestire i database DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 655a67aa-d662-42f2-b982-c6217125ada8
caps.latest.revision: 14
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 14
---
# Gestire i database DQS
  In questa sezione vengono fornite le informazioni sulle attività di gestione di database che possono essere eseguite nei database DQS, ad esempio il backup e il ripristino oppure il collegamento o lo scollegamento.  
  
##  <a name="BackupRestore"></a> Backup e ripristino dei database DQS  
 Le operazioni di backup e di ripristino dei database di SQL Server sono operazioni comuni che gli amministratori di database eseguono per impedire la perdita di dati in caso di emergenza recuperando i dati dai database di backup. [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] viene implementato principalmente con due database di SQL Server: DQS_MAIN e DQS_PROJECTS. Le procedure di backup e ripristino dei database di [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) sono simili a quelle degli altri database di SQL Server. Esistono tuttavia tre problemi associati al backup e al ripristino dei database DQS:  
  
-   Le operazioni di backup e di ripristino dei database di DQS devono essere sincronizzate. In caso contrario, la versione ripristinata del [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] non funzionerà.  
  
-   I due database di DQS, DQS_MAIN e DQS_PROJECTS, contengono gli assembly e gli altri oggetti complessi, oltre agli oggetti di database semplici, ad esempio tabelle e stored procedure.  
  
-   Esistono alcune entità al di fuori dei database di DQS che devono essere presenti affinché i database di questo tipo funzionino come [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], in particolare i due account di accesso di SQL Server (##MS_dqs_db_owner_login## e ##MS_dqs_service_login##) e una stored procedure di inizializzazione (DQInitDQS_MAIN) nel database master.  
  
 Per informazioni dettagliate sul backup e il ripristino in SQL Server, vedere [Back Up and Restore of SQL Server Databases](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
### Impostare in modo predefinito l'aumento automatico delle dimensioni e il modello di recupero per i database di DQS  
 Per impedire una crescita smisurata dei database di DQS e dei log delle transazioni e un conseguente riempimento potenziale del disco rigido:  
  
-   Le dimensioni predefinite relative all'aumento automatico dei database di DQS vengono impostate su 10%. ****  
  
-   Il modello di recupero predefinito dei database di DQS viene impostato su **Con registrazione minima**. Nel modello di recupero con registrazione minima, per le transazioni è prevista la registrazione minima. Si verifica automaticamente il troncamento del log al termine della transazione per liberare spazio nel log delle transazioni (file con estensione ldf). Per informazioni dettagliate sul modello di recupero con registrazione minima, vedere [backup completo del Database & #40; SQL Server & #41;](../relational-databases/backup-restore/full-database-backups-sql-server.md).  
  
> [!IMPORTANT]  
>  -   Nel modello di recupero con registrazione minima, se i record del log rimangono inattivi per molto tempo, ad esempio una transazione lunga e dispendiosa in termini di tempo, il troncamento del log può essere ritardato e pertanto può determinare il riempimento del log delle transazioni. Inoltre, il troncamento del log non comporta una riduzione delle dimensioni del file di log fisico (file con estensione ldf). Per ridurre le dimensioni di un file di log fisico, è necessario compattare il file di log. Per informazioni sulla risoluzione dei problemi riguardanti i log delle transazioni, vedere [Log delle transazioni & #40; SQL Server & #41;](../relational-databases/logs/the-transaction-log-sql-server.md) l'articolo di supporto Microsoft o [http://go.microsoft.com/fwlink/?LinkId=237446](http://go.microsoft.com/fwlink/?LinkId=237446).  
> -   È necessario eseguire regolarmente un backup completo o differenziale dei database di DQS e un backup del log delle transazioni, nonché effettuare un recupero temporizzato dei dati. Per ulteriori informazioni, vedere [backup completo del Database & #40; SQL Server & #41;](../relational-databases/backup-restore/full-database-backups-sql-server.md) e [eseguire il backup di un Log delle transazioni & #40; SQL Server & #41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).  
  
##  <a name="DetachAttach"></a> Scollegare o collegare i database DQS  
 È possibile scollegare i dati e i file di log delle transazioni dei database DQS, quindi ricollegare i database alla stessa istanza o a un'altra istanza di SQL Server se si desidera impostare i database DQS su un'istanza diversa di SQL Server nello stesso computer oppure spostare il database.  
  
 Per informazioni dettagliate sugli aspetti da considerare prima e durante lo scollegamento e collegamento di database in SQL Server, vedere [scollegare il Database e Allega & #40; SQL Server & #41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
## Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene descritto come eseguire il backup e il ripristino dei database di DQS.|[Backup e ripristino di database DQS](../data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|Viene descritto come scollegare e collegare i database DQS.|[Detaching and Attaching DQS Databases](../data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## Vedere anche  
 [Amministrazione DQS](../data-quality-services/dqs-administration.md)  
  
  