---
title: "Cenni preliminari sulla sicurezza (SQL Server R Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# Cenni preliminari sulla sicurezza (SQL Server R Services)

In questo argomento viene descritta l'architettura di protezione generale che viene utilizzato per connettere il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] dal database e componenti correlati al runtime di R. Vengono forniti esempi del processo di protezione per due scenari comuni per l'uso di R in un ambiente aziendale:

+ L'esecuzione di funzioni RevoScaleR in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] da un client di analisi scientifica dei dati
+ Esecuzione R direttamente da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] utilizzando stored procedure

## Panoramica della sicurezza

Oggetto [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] account di accesso o account utente di Windows è necessario eseguire tutti i processi R che utilizzano [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. Identifica l'account di accesso o utente di *entità di sicurezza*, che deve disporre dell'autorizzazione per accedere al database di cui è in esecuzione R, nonché le autorizzazioni per leggere dati da oggetti protetti, ad esempio tabelle, o per scrivere nuovi dati o aggiungere nuovi oggetti, se richiesto dal processo di R.

Pertanto, è un requisito che ogni persona che esegue il codice R contro [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] deve essere mappato a un account di accesso nel database, indipendentemente dal fatto che il codice viene inviato da un client di analisi scientifica dei dati remoti tramite le funzioni RevoScaleR o all'uso di una procedura T-SQL archiviati. 

Si supponga ad esempio è creato il codice R che viene eseguito sul computer portatile, che si desidera eseguire il codice [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. È necessario assicurarsi che siano soddisfatte le condizioni seguenti:

+ Il database consente le connessioni remote.
+ Un account di accesso SQL con il nome e la password utilizzata nel codice R è stato aggiunto il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] a livello di istanza. In alternativa, se si utilizza l'autenticazione integrata di Windows, l'utente di Windows specificato nella stringa di connessione deve essere aggiunto come utente nell'istanza.
+ L'account di accesso SQL o un utente di Windows deve disporre dell'autorizzazione per eseguire script esterni. In genere, questa autorizzazione può essere aggiunti solo da un amministratore del database.
+ Finestra utente o accesso SQL deve essere aggiunto come utente con autorizzazioni appropriate, in ogni database in cui il processo di R esegue una qualsiasi di queste operazioni:
    + Recupero di dati
    + Scrittura o aggiornamento dei dati 
    + Creazione di nuovi oggetti, ad esempio tabelle o le stored procedure

Dopo che l'account di accesso o l'account utente di Windows è stato eseguito il provisioning e dispone delle autorizzazioni necessarie, è possibile eseguire codice R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] utilizzando un oggetto di origine di dati R o chiamate di stored procedure. Ogni volta che viene avviata R da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], la sicurezza del motore di database Ottiene il contesto di sicurezza dell'utente che ha avviato il processo di R e gestisce i mapping dell'utente o account di accesso agli oggetti a protezione diretta. 

Pertanto, tutti i processi R avviate da un client remoto è necessario specificare le informazioni di accesso o utente come parte della stringa di connessione.


## Interazione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] protezione e finestra di avvio

Quando viene eseguito uno script R nel contesto del [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer, il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio Ottiene un account di lavoro disponibili (un account utente locale) da un pool di account di lavoro stabilito per processo esterno e utilizza tale account di lavoro per eseguire le attività correlate. 

Ad esempio, se si avvia un processo R con le credenziali di dominio di Windows, l'account potrebbe essere connessa all'account di lavoro di avvio *SQLRUser01*.

Dopo il mapping a un account di lavoro, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Crea un token utente utilizzato per avviare i processi. 

Quando tutti [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] vengono completate le operazioni, l'account utente di lavoro verrà contrassegnato come liberi e restituita al pool.

Per ulteriori informazioni su [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], vedere [nuovi componenti in SQL Server per R supportano l'integrazione](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r-services.md).

## Protezione degli account di lavoro
Questo mapping di un utente esterno di Windows o account di accesso SQL valido a un account di lavoro è valido solo per la durata della durata della query SQL che esegue lo script R. 

Query parallele dall'account di accesso stesso viene eseguito il mapping all'account di lavoro utente stesso.

La directory utilizzata per i processi sono gestite dal [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] utilizzando RLauncher, e directory sono l'accesso limitato. L'account di lavoro non può accedere ai file nelle cartelle sopra il proprio, ma può leggere, scrivere o eliminare gli elementi figlio sotto la cartella di lavoro di sessione che è stato creato per la query SQL con script R.

Per ulteriori informazioni su come modificare il numero di account di lavoro, i nomi di account o le password degli account, vedere [modificare il Pool degli Account utente per i servizi di SQL Server R](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).


## Isolamento di sicurezza per più script esterni

Il meccanismo di isolamento si basa sugli account utente fisico. Come per un linguaggio specifico di runtime vengono avviati i processi di satellite, ogni attività satellite utilizza l'account di lavoro specificato dal [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Se un'attività richiede più satelliti, ad esempio, nel caso di query parallele, un account singolo lavoro viene utilizzato per tutte le attività correlate.

Nessun account di lavoro possa vedere o modificare i file utilizzati da altri account di lavoro.
 
Se si è un amministratore del computer, è possibile visualizzare le directory create per ogni processo. Ogni directory è identificato dal relativo GUID di sessione.

## Vedere anche
[Panoramica dell'architettura](../../advanced-analytics/r-services/architecture-overview-sql-server-r-services.md)