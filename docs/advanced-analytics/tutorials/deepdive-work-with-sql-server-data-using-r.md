---
title: Usare i dati di SQL Server con R (amp;#40;procedura approfondita di R e SQL) | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a59d467417c3471fa643acf9fc65ab45d5dc7a45
ms.sourcegitcommit: df3923e007527ce79e2d05821b62d77ee06fd655
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2018
ms.locfileid: "44375674"
---
# <a name="lesson-1-create-a-database-and-permissions"></a>Lezione 1: Creare un database e autorizzazioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo fa parte il [esercitazione RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md) su come usare [funzioni RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) con SQL Server.

In questa lezione, configurare l'ambiente e aggiungere i dati che necessari per il training dei modelli ed eseguiti riepiloghi rapidi dei dati. Come parte del processo, è necessario completare queste attività:
  
- Creare un nuovo database in cui archiviare i dati per il training e assegnare i punteggi ai due modelli R.
  
- Creare un account,che sia un utente di Windows o account di accesso SQL, per consentire la comunicazione tra la workstation e il computer con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
- Creare origini dati in R da usare con i dati e gli oggetti di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
- Usare l'origine di dati R per caricare i dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
- Usare R per ottenere un elenco di variabili e modificare i metadati della tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .
  
- Creare un contesto di calcolo per consentire l'esecuzione remota di codice R.
  
- (Facoltativo) Abilitare la traccia sul contesto di calcolo remoto.
  
## <a name="create-the-database-and-user"></a>Creare il database e l'utente

Per questa procedura dettagliata, creare un nuovo database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]e aggiungere un account di accesso SQL con le autorizzazioni per scrivere e leggere i dati e di eseguire script R.

> [!NOTE]
> Se si legge solo i dati, l'account che esegue gli script R che è necessarie autorizzazioni SELECT (**db_datareader** ruolo) nel database specificato. In questa esercitazione, tuttavia, è necessario disporre dei privilegi di amministratore DDL per preparare il database e creare tabelle per salvare i risultati di punteggio.
> 
> Inoltre, se non si è il proprietario del database, è necessaria l'autorizzazione, EXECUTE ANY EXTERNAL SCRIPT, per poter eseguire gli script R.

1. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]selezionare l'istanza in cui [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] è abilitato, fare clic con il pulsante destro del mouse su **Database**e selezionare **Nuovo database**.
  
2. Digitare un nome per il nuovo database. È possibile usare un nome qualsiasi. Ricordarsi tuttavia di modificare di conseguenza tutti gli script [!INCLUDE[tsql](../../includes/tsql-md.md)] e R usati in questa procedura.
  
    > [!TIP]
    > Per visualizzare il nome del database aggiornato, fare clic con il pulsante destro del mouse su **Database** e selezionare **Aggiorna** .
  
3. Selezionare **Nuova query**e modificare il contesto del database sul database master.
  
4. Nella nuova finestra **Query** , eseguire i comandi seguenti per creare gli account utente e assegnarli al database usato in questa esercitazione. Assicurarsi di modificare il nome del database, se necessario.
  
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

5. Per verificare che l'utente sia stato creato, selezionare il nuovo database, espandere **Sicurezza**ed espandere **Utenti**.

## <a name="troubleshooting"></a>Risoluzione dei problemi

In questa sezione sono elencati alcuni problemi comuni che possono verificarsi durante l'impostazione del database.

- **Come è possibile verificare la connettività del database e controllare le query SQL?**
  
    È possibile che, prima di eseguire il codice R tramite il server, si voglia controllare che il database sia raggiungibile dall'ambiente di sviluppo R. Entrambi [Esplora Server di Visual Studio](https://msdn.microsoft.com/library/x603htbk.aspx) e [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) sono strumenti gratuiti con connettività di database e funzionalità di gestione molto efficienti.
  
    Se non si vogliono installare altri strumenti di gestione del database, è possibile creare una connessione di test per l'istanza di SQL Server usando l' [Amministrazione origine dati ODBC](https://msdn.microsoft.com/library/ms714024.aspx) in Pannello di controllo. Se il database è configurato correttamente e il nome utente e la password specificati sono corretti, sarà possibile visualizzare il database appena creato e selezionarlo come database predefinito.
  
    Se non è possibile connettersi al database, verificare che le connessioni remote siano abilitate per il server e che sia stato abilitato il protocollo Named Pipes. In questo articolo vengono fornite ulteriori suggerimenti sulla risoluzione dei problemi: [risolvere i problemi di connessione al motore di Database di SQL Server](https://docs.microsoft.com/sql/database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine).
  
- **Il nome della tabella datareader è preceduto dal prefisso it. Perché?**
  
    Quando si specifica lo schema predefinito per questo utente come **db_datareader**, tutte le tabelle e altri nuovi oggetti creati da questo utente hanno come prefisso il *schema* nome. Uno schema è una sorta di cartella. Può essere aggiunto a un database per organizzare gli oggetti. Lo schema definisce anche i privilegi dell'utente all'interno del database.
  
    Quando lo schema è associato un nome utente specifico, l'utente è il _proprietario dello schema_. Ogni volta che si crea un oggetto, l'oggetto sarà sempre creato in base al proprio schema, a meno che non si chieda specificatamente di crearlo in un altro schema.
  
    Ad esempio, se si crea una tabella con il nome **TestData**, e lo schema predefinito è **db_datareader**, la tabella viene creata con il nome `<database_name>.db_datareader.TestData`.
  
    Per questo motivo, un database può contenere più tabelle con lo stesso nome, purché le tabelle appartengano a schemi diversi.
   
    Se si sta cercando una tabella e non si specifica uno schema, il server di database cercherà uno schema che si è proprietari. Non è pertanto necessario specificare il nome dello schema quando si accede a tabelle di uno schema associato al proprio account di accesso.
  
- **Non ho privilegi DLL. Posso comunque seguire l'esercitazione**?
  
    Sì, però è necessario chiedere a un altro utente di precaricare i dati nelle tabelle di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e saltare le sezioni che richiedono la creazione di tabelle nuove. Le funzioni che richiedono privilegi DDL sono indicate nell'esercitazione laddove possibile.

    Inoltre, chiedere all'amministratore di concedere l'autorizzazione EXECUTE ANY EXTERNAL SCRIPT. È necessario per l'esecuzione di script R, se è remoto oppure usando `sp_execute_external_script`.

## <a name="next-step"></a>Passaggio successivo

[Creare oggetti dati di SQL Server usando RxSqlServerData](../../advanced-analytics/tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)

## <a name="overview"></a>Panoramica

[Procedura approfondita per l'analisi scientifica dei dati: Uso dei pacchetti RevoScaleR](../../advanced-analytics/tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)



