---
title: Gestire database DQS | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology:
- data-quality-services
ms.topic: conceptual
ms.assetid: 655a67aa-d662-42f2-b982-c6217125ada8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: dc31a6b98c12b948dd353ca7f7839f5a1fb0dc04
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51696740"
---
# <a name="manage-dqs-databases"></a>Manage DQS Databases

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In questa sezione vengono fornite le informazioni sulle attività di gestione di database che possono essere eseguite nei database DQS, ad esempio il backup e il ripristino oppure il collegamento o lo scollegamento.  
  
##  <a name="BackupRestore"></a> Backup e ripristino dei database DQS  
 Le operazioni di backup e di ripristino dei database di SQL Server sono operazioni comuni che gli amministratori di database eseguono per impedire la perdita di dati in caso di emergenza recuperando i dati dai database di backup. Il[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] viene implementato principalmente con due database di SQL Server: DQS_MAIN e DQS_PROJECTS. Le procedure di backup e ripristino dei database di [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) sono simili a quelle degli altri database di SQL Server. Esistono tuttavia tre problemi associati al backup e al ripristino dei database DQS:  
  
-   Le operazioni di backup e di ripristino dei database di DQS devono essere sincronizzate. In caso contrario, la versione ripristinata del [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] non funzionerà.  
  
-   I due database di DQS, DQS_MAIN e DQS_PROJECTS, contengono gli assembly e gli altri oggetti complessi, oltre agli oggetti di database semplici, ad esempio tabelle e stored procedure.  
  
-   Esistono alcune entità al di fuori dei database di DQS che devono essere presenti affinché i database di questo tipo funzionino come [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], in particolare i due account di accesso di SQL Server (##MS_dqs_db_owner_login## e ##MS_dqs_service_login##) e una stored procedure di inizializzazione (DQInitDQS_MAIN) nel database master.  
  
 Per informazioni dettagliate sul backup e il ripristino in SQL Server, vedere [Backup e ripristino di database SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).  
  
### <a name="default-autogrowth-size-and-recovery-model-for-the-dqs-databases"></a>Impostare in modo predefinito l'aumento automatico delle dimensioni e il modello di recupero per i database di DQS  
 Per impedire una crescita smisurata dei database di DQS e dei log delle transazioni e un conseguente riempimento potenziale del disco rigido:  
  
-   Le dimensioni predefinite relative **all'aumento automatico** dei database di DQS vengono impostate su 10%.  
  
-   Il modello di recupero predefinito dei database di DQS viene impostato su **Con registrazione minima**. Nel modello di recupero con registrazione minima, per le transazioni è prevista la registrazione minima. Si verifica automaticamente il troncamento del log al termine della transazione per liberare spazio nel log delle transazioni (file con estensione ldf). Per informazioni sul modello di recupero con registrazione minima, vedere [Backup completo del database &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md).  
  
> [!IMPORTANT]  
>  -   Nel modello di recupero con registrazione minima, se i record del log rimangono inattivi per molto tempo, ad esempio una transazione lunga e dispendiosa in termini di tempo, il troncamento del log può essere ritardato e pertanto può determinare il riempimento del log delle transazioni. Inoltre, il troncamento del log non comporta una riduzione delle dimensioni del file di log fisico (file con estensione ldf). Per ridurre le dimensioni di un file di log fisico, è necessario compattare il file di log. Per informazioni sulla risoluzione dei problemi riguardanti il log delle transazioni, vedere [Log delle transazioni &#40;SQL Server&#41;](../relational-databases/logs/the-transaction-log-sql-server.md) o l'articolo del Supporto tecnico Microsoft all'indirizzo [https://go.microsoft.com/fwlink/?LinkId=237446](https://go.microsoft.com/fwlink/?LinkId=237446).  
> -   È necessario eseguire regolarmente un backup completo o differenziale dei database di DQS e un backup del log delle transazioni, nonché effettuare un recupero temporizzato dei dati. Per altre informazioni, vedere [Backup completo del database & #40; SQL Server & #41; ](../relational-databases/backup-restore/full-database-backups-sql-server.md) e [Backup di un log delle transazioni & #40; SQL Server & #41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).  
  
##  <a name="DetachAttach"></a> Scollegare o collegare i database DQS  
 È possibile scollegare i dati e i file di log delle transazioni dei database DQS, quindi ricollegare i database alla stessa istanza o a un'altra istanza di SQL Server se si desidera impostare i database DQS su un'istanza diversa di SQL Server nello stesso computer oppure spostare il database.  
  
 Per informazioni dettagliate sui fattori da considerare prima e durante lo scollegamento e il collegamento dei database in SQL Server, vedere [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene descritto come eseguire il backup e il ripristino dei database di DQS.|[Backup e ripristino di database DQS](../data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|Viene descritto come scollegare e collegare i database DQS.|[Scollegamento e collegamento di database DQS](../data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione DQS](../data-quality-services/dqs-administration.md)  
  
  
