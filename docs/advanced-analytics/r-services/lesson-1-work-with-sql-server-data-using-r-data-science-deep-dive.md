---
title: "Lezione 1: Usare i dati SQL Server con R (Procedura approfondita per l&#39;analisi scientifica dei dati) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "09/30/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 0a3d7ba0-4113-4cde-9645-debba45cae8f
caps.latest.revision: 20
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 20
---
# Lezione 1: Usare i dati SQL Server con R (Procedura approfondita per l&#39;analisi scientifica dei dati)
In questa lezione verrà impostato l'ambiente e saranno aggiunti i dati necessari per il training dei modelli. Saranno anche eseguiti riepiloghi rapidi dei dati. Il processo prevede che siano completate le attività seguenti:  
  
-   Creare un nuovo database in cui archiviare i dati per il training e assegnare i punteggi ai due modelli R.  
  
-   Creare un account,che sia un utente di Windows o account di accesso SQL, per consentire la comunicazione tra la workstation e il computer con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Creare origini dati in R da usare con i dati e gli oggetti di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Usare l'origine di dati R per caricare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Usare R per ottenere un elenco di variabili e modificare i metadati della tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Creare un contesto di calcolo per consentire l'esecuzione remota di codice R.  
  
-   Sapere come abilitare la traccia sul contesto di calcolo remoto.  
  
## Creare il database e l'utente  
In questa procedura dettagliata sarà creato un database nuovo in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e sarà aggiunto un account di accesso SQL con le autorizzazioni per scrivere, leggere i dati ed eseguire script R.  
  
> [!NOTE]  
> Se l'account che esegue gli script R si limita alla sola letture dei dati, è sufficiente che abbia solo autorizzazioni SELECT per il database specificato (ruolo**db_datareader**). In questa esercitazione saranno comunque necessari privilegi di amministratore DDL per preparare il database e creare le tabelle in cui salvare i risultati dell'assegnazione dei punteggi.  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] selezionare l'istanza in cui [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è abilitato, fare clic con il pulsante destro del mouse su **Database** e selezionare **Nuovo database**.  
  
2.  Digitare un nome per il nuovo database. È possibile usare un nome qualsiasi. Ricordarsi tuttavia di modificare di conseguenza tutti gli script [!INCLUDE[tsql](../../includes/tsql-md.md)] e R usati in questa procedura.  
  
    > [!TIP]  
    > Per visualizzare il nome del database aggiornato, fare clic con il pulsante destro del mouse su **Database** e selezionare **Aggiorna**.  
  
3.  Selezionare **Nuova query** e modificare il contesto del database sul database master.  
  
4.  Nella nuova finestra **Query**, eseguire i comandi seguenti per creare gli account utente e assegnarli al database usato in questa esercitazione. Assicurarsi di modificare il nome del database, se necessario.   
  
**Utente di Windows**  
  
```SQL  
 -- Create server user based on Windows account  
USE master  
GO   
CREATE LOGIN [<DOMAIN>\<user_name>] FROM WINDOWS WITH DEFAULT_DATABASE=[DeepDive]  
  
 --Add the new user to tutorial database  
USE [DeepDive]  
GO  
CREATE USER [<user_name>] FOR LOGIN [<DOMAIN>\<user_name>] WITH DEFAULT_SCHEMA=[db_datareader]   
``` 
  
**Account di accesso SQL**  
  
```SQL 
-- Create new SQL login  
USE master  
GO   
CREATE LOGIN DDUser01 WITH PASSWORD='<type password here>', CHECK_EXPIRATION=OFF, CHECK_POLICY=OFF;   

-- Add the new SQL login to tutorial database     
USE [DeepDive]  
GO 
CREATE USER [DDUser01] FOR LOGIN [DDUser01] WITH DEFAULT_SCHEMA=[db_datareader]     
```  
  
5.  Per verificare che l'utente sia stato creato, selezionare il nuovo database, espandere **Sicurezza** ed espandere **Utenti**.  
  
## Risoluzione dei problemi  
In questa sezione sono elencati alcuni problemi comuni che possono verificarsi durante l'impostazione del database.  
  
-   **Come è possibile verificare la connettività del database e controllare le query SQL?**  
  
    È possibile che, prima di eseguire il codice R tramite il server, si voglia controllare che il database sia raggiungibile dall'ambiente di sviluppo R. Entrambi [Esplora Server di Visual Studio](https://msdn.microsoft.com/library/x603htbk.aspx) e [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) sono strumenti gratuiti con connettività di database e funzionalità di gestione molto efficienti.  
  
    Se non si vogliono installare altri strumenti di gestione del database, è possibile creare una connessione di test per l'istanza di SQL Server usando l'[Amministrazione origine dati ODBC](https://msdn.microsoft.com/library/ms714024.aspx) in Pannello di controllo. Se il database è configurato correttamente e il nome utente e la password specificati sono corretti, sarà possibile visualizzare il database appena creato e selezionarlo come database predefinito.  
  
    Se non è possibile connettersi al database, verificare che le connessioni remote siano abilitate per il server e che sia stato abilitato il protocollo Named Pipes. Leggere [questo articolo](http://social.technet.microsoft.com/wiki/contents/articles/2102.how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx) per altri suggerimenti sulla risoluzione dei problemi.  
  
-   **Il nome della tabella datareader è preceduto dal prefisso it. Perché?**  
  
    Se si specifica che lo schema predefinito per questo utente sia **db_datareader**, tutte le tabelle e tutti gli altri nuovi oggetti creati da questo utente saranno preceduti dal prefisso definito con questo *schema*. Uno schema è una sorta di cartella. Può essere aggiunto a un database per organizzare gli oggetti. Lo schema definisce anche i privilegi dell'utente all'interno del database.  
  
    Quando lo schema è associato a un nome utente specifico, tale utente diventa il proprietario dello schema. Ogni volta che si crea un oggetto, l'oggetto sarà sempre creato in base al proprio schema, a meno che non si chieda specificatamente di crearlo in un altro schema.  
  
    Ad esempio, se si crea una tabella con il nome *TestData* e lo schema predefinito è **db_datareader**, la tabella verrà creata con il nome *<database_name>.db_datareader.TestData*.  
  
    Per questo motivo, un database può contenere più tabelle con lo stesso nome, purché le tabelle appartengano a schemi diversi.   
   
    Se si cerca una tabella senza specificare uno schema, il server di database cercherà uno schema di cui si è proprietari. Non è pertanto necessario specificare il nome dello schema quando si accede a tabelle di uno schema associato al proprio account di accesso.   
  
-   **Non ho privilegi DLL. Posso comunque seguire l'esercitazione**?  
  
    Sì, però è necessario chiedere a un altro utente di precaricare i dati nelle tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e saltare le sezioni che richiedono la creazione di tabelle nuove. Le funzioni che richiedono privilegi DDL sono in genere specificate in questa esercitazione.  
  
  
## Passaggio successivo  
[Creare oggetti dati di SQL Server usando RxSqlServerData](../../advanced-analytics/r-services/create-sql-server-data-objects-using-rxsqlserverdata.md)  
  
## Passaggio precedente  
[Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)  
  
## Vedere anche  
[Procedura approfondita per l'analisi scientifica dei dati](http://msdn.microsoft.com/library/mt637368(SQL.130).aspx)  
  
  
  
