---
title: "Visualizzazione o modifica del modello di recupero di un database (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "backup di database [SQL Server], modelli di recupero"
  - "recupero [SQL Server], modello di recupero"
  - "backup di database [SQL Server], modelli di recupero"
  - "modello di recupero [SQL Server], cambio"
  - "modelli di recupero (SQL Server), visualizzazione"
  - "ripristini di database [SQL Server], modelli di recupero"
  - "modifica di modelli di recupero di database"
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
caps.latest.revision: 40
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 40
---
# Visualizzazione o modifica del modello di recupero di un database (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Questo argomento illustra come visualizzare o modificare il database usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. 
  
  Un *modello di recupero* è una proprietà del database che determina la modalità di registrazione delle transazioni, se è necessario e possibile eseguire il backup del log delle transazioni e quali tipi di operazioni di ripristino sono disponibili. Sono tre i modelli di recupero disponibili: con registrazione minima, con registrazione completa e con registrazione minima delle operazioni bulk. In genere, un database utilizza il modello di recupero con registrazione completa o con registrazione minima. In un database è possibile passare a un modello di recupero diverso in qualsiasi momento. Il database **modello** imposta il modello di recupero predefinito dei nuovi database.  
  
  Per una spiegazione più dettagliata dei [modelli di recupero](https://msdn.microsoft.com/library/ms189275.aspx), vedere [SQL Server Recovery Models (Modelli di recupero di SQL Server)](https://www.mssqltips.com/sqlservertutorial/2/sql-server-recovery-models/) a cura degli esperti di [MSSQLTips!](https://www.mssqltips.com/)
  
  
##  <a name="BeforeYouBegin"></a> Operazioni preliminari  
  

-   **Prima** di passare dal [modello di recupero con registrazione completa o con registrazione minima delle operazioni bulk](https://msdn.microsoft.com/library/ms189275.aspx), [eseguire il backup del log delle transazioni](https://msdn.microsoft.com/library/ms179478.aspx).  
  
-   Il recupero temporizzato non è possibile con il modello di recupero con registrazione minima delle operazioni bulk. L'esecuzione di transazioni nel modello di recupero con registrazione minima delle operazioni bulk che richiedono il ripristino di un log delle transazioni potrebbe esporle alla perdita di dati. Per ottimizzare la recuperabilità in uno scenario di recupero di emergenza, passare al modello di recupero con registrazione minima delle operazioni bulk esclusivamente nelle condizioni seguenti:  
  
    -   Agli utenti non è attualmente consentito l'accesso al database.  
  
    -   Tutte le modifiche effettuate durante l'elaborazione bulk possano essere recuperate senza dipendere da un backup del log, ad esempio ripetendo i processi bulk.  
  
     Se queste due condizioni sono soddisfatte, l'utente non sarà esposto ad alcuna perdita di dati durante il ripristino di un log delle transazioni di cui è stato eseguito il backup nel modello di recupero con registrazione minima delle operazioni bulk.  
  
**Nota.** Se si passa al modello di recupero con registrazione completa durante un'operazione in blocco, la registrazione dell'operazione in blocco cambia da registrazione minima a completa, e viceversa.  
  
###  <a name="Security"></a> Autorizzazioni necessarie  
   È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per visualizzare o modificare il modello di recupero  
  
1.  Dopo aver effettuato la connessione all'istanza appropriata del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Esplora oggetti fare clic sul nome del server per espanderne l'albero.  
  
2.  Espandere **Database**e, a seconda del database, selezionare un database utente o espandere **Database di sistema** e selezionare un database di sistema.  
  
3.  Fare clic con il pulsante destro del mouse sul database e quindi scegliere **Proprietà** per visualizzare la finestra di dialogo **Proprietà database**.  
  
4.  Nel riquadro **Selezione pagina** fare clic su **Opzioni**.  
  
5.  Il modello di recupero attualmente implementato è visualizzato nella casella di riepilogo **Modello di recupero** .  
  
6.  Se desiderato, è possibile modificare il modello di recupero selezionandone uno differente nell'elenco. Le scelte possibili sono **Con registrazione completa**, **Con registrazione minima delle operazioni bulk** e **Con registrazione minima**.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per visualizzare il modello di recupero  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio viene mostrato come eseguire una query sulla vista del catalogo [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) per individuare il modello di recupero del database **model** .  
  
```tsql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### Per modificare il modello di recupero  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio viene mostrato come impostare il modello di recupero nel database `model` su `FULL` utilizzando l'opzione `SET RECOVERY` dell'istruzione [ALTER DATABASE](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md) .  
  
```tsql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="FollowUp"></a> Indicazioni: dopo la modifica del modello di recupero  
  
-   **Dopo il passaggio tra i modelli di recupero con registrazione completa e con registrazione minima delle operazioni bulk**  
  
    -   Dopo il completamento delle operazioni bulk, tornare immediatamente alla modalità di recupero con registrazione completa.  
  
    -   Dopo il passaggio dal modello di recupero con registrazione minima delle operazioni bulk al modello di recupero con registrazione completa, eseguire il backup del log.  
  
        >**NOTA:** la strategia di backup rimane invariata, cioè continua l'esecuzione di backup del database, del log e differenziali periodici.  
  
-   **Dopo il passaggio dal modello di recupero con registrazione minima**  
  
    -   Immediatamente dopo il passaggio al modello di recupero con registrazione completa o con registrazione minima delle operazioni bulk, eseguire un backup di database completo o differenziale per avviare la catena di log.  
  
        >**NOTA:** il passaggio al modello di recupero con registrazione completa o con registrazione minima delle operazioni bulk ha effetto solo dopo il primo backup dei dati.  
  
    -   Pianificare backup regolari dei log e aggiornare il piano di ripristino di conseguenza.  
  
        > **IMPORTANTE** Eseguire il backup dei log. Se non si esegue il backup del log con la necessaria frequenza, il log delle transazioni può espandersi fino a esaurire lo spazio su disco.  
  
-   **Dopo il passaggio al modello di recupero con registrazione minima**  
  
    -   Interrompere tutti i processi pianificati per l'esecuzione del backup del log delle transazioni.  
  
    -   Verificare la pianificazione di backup di database periodici. Il backup del database è essenziale sia per proteggere i dati sia per troncare la porzione inattiva del log delle transazioni.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Creare un backup completo del database &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [Eseguire il backup di un log delle transazioni &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
-   [Creazione di un processo](../../ssms/agent/create-a-job.md)  
  
-   [Abilitare o disabilitare un processo](../../ssms/agent/disable-or-enable-a-job.md)  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
  
-   [Database Maintenance Plans](http://msdn.microsoft.com/library/ms187658.aspx) nella documentazione online di [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
## Vedere anche  
 [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [Modelli di recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)  
  
  