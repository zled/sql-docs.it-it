---
title: "Backup e ripristino di database DQS | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f3091f62-2234-4a80-a615-cf14c2a1da85
caps.latest.revision: 12
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 12
---
# Backup e ripristino di database DQS
  In questo argomento viene descritto come eseguire il backup e il ripristino dei database DQS.  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti  
  
-   È necessario conoscere o ricordare la password per la chiave master del database fornita durante l'installazione del server DQS.  
  
-   Assicurarsi che non vi siano attività o processi in esecuzione in DQS. È possibile verificare utilizzando la schermata **Monitoraggio attività** . Per informazioni dettagliate su funzionamento di questa schermata, vedere [Monitor DQS Activities](../data-quality-services/monitor-dqs-activities.md).  
  
-   Assicurarsi che non vi siano utenti connessi al server DQS.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
  
-   Per poter effettuare operazioni di backup e ripristino, è necessario che l'account utente di Windows sia membro del ruolo predefinito del server sysadmin nell'istanza di SQL Server in cui è installato.  
  
-   È necessario disporre del ruolo dqs_administrator sul database DQS_MAIN per interrompere qualsiasi attività in esecuzione o arrestare processi in corso in DQS.  
  
##  <a name="BackupRestore"></a> Backup e ripristino di database DQS  
  
1.  Avviare Microsoft SQL Server Management Studio e connettersi all'istanza di SQL Server appropriata.  
  
2.  In Esplora oggetti espandere il nodo **Database** .  
  
3.  Eseguire il backup del database DQS_STAGING_DATA. Per istruzioni dettagliate per il backup di un database di SQL Server, vedere [Crea un Backup completo del Database & #40; SQL Server & #41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).  
  
4.  Eseguire il backup del database DQS_PROJECTS.  
  
5.  Eseguire il backup del database DQS_MAIN.  
  
6.  Disconnettersi dall'istanza corrente di SQL Server e connettersi all'istanza di SQL Server in cui si desidera ripristinare i database.  
  
7.  Ripristinare il database DQS_MAIN. Per istruzioni dettagliate ripristinare un database di SQL Server, vedere [ripristinare un Database di Backup utilizzando SQL Server Management Studio](../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md).  
  
8.  Ripristinare il database DQS_PROJECTS.  
  
9. Ripristinare il database DQS_STAGING_DATA.  
  
10. In Esplora oggetti, fare doppio clic su server e quindi fare clic su **Nuova Query**.  
  
11. Nella finestra dell'Editor di Query, copiare le istruzioni SQL e sostituire *\< PASSWORD>* con la password fornita durante l'installazione di DQS per la chiave master del database:  
  
    ```  
    USE [DQS_MAIN]  
    GO  
    EXECUTE [internal_core].[RestoreDQDatabases] '<PASSWORD>'  
    GO  
  
    ```  
  
12. Premere F5 per eseguire le istruzioni. Esaminare il riquadro dei risultati ** ** per verificare che le istruzioni siano state eseguite correttamente.  
  
## Vedere anche  
 [Gestire i database DQS](../data-quality-services/manage-dqs-databases.md)  
  
  