---
title: Cenni preliminari sulla sicurezza per Python in SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 11/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: "9"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: f3d104425953774583602492da6ea65fddb8b837
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2017
---
# <a name="security-overview-for-python-in-sql-server"></a>Cenni preliminari sulla sicurezza per Python in SQL Server

In questo argomento viene descritta l'architettura di sicurezza che viene utilizzato per connettere il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] dal database e i componenti di Python. Vengono forniti esempi del processo di protezione per due scenari comuni: esecuzione di Python in SQL Server utilizzando una stored procedure e l'esecuzione di Python con SQL Server come contesto di calcolo remoto.

## <a name="security-overview"></a>Cenni preliminari sulla sicurezza

Oggetto [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] account di accesso o account utente di Windows è necessario per eseguire script Python in SQL Server. Questi *entità di sicurezza* vengono gestite a livello di istanza e database e identificare gli utenti che dispongono dell'autorizzazione per connettersi al database, leggere e scrivere dati o creare oggetti di database quali tabelle e stored procedure. Inoltre, gli utenti che eseguono script Python devono disporre dell'autorizzazione per l'esecuzione dello script esterno a livello di database.

Se l'utente deve eseguire Python codice nel database, o oggetti di database di access e i dati, anche gli utenti che utilizzano Python in uno strumento esterno devono essere mappati a un account di accesso o un account nel database. Se lo script Python viene inviato da un client di analisi scientifica dei dati remota o avviate tramite una procedura T-SQL archiviati, sono necessarie le autorizzazioni stesso.

Si supponga, ad esempio, che è stato creato uno script Python eseguito in un computer portatile, e si desidera eseguire il codice di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. È necessario assicurarsi che siano soddisfatte le condizioni seguenti:

+ Il database consente le connessioni remote.
+ L'account di accesso SQL o l'account di Windows utilizzato per l'accesso al database è stato aggiunto il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] a livello di istanza.
+ È necessario concedere all'account di accesso SQL o all'utente di Windows l'autorizzazione per eseguire gli script esterni. In genere, questa autorizzazione può essere aggiunta solo da un amministratore del database.
+ L'account di accesso SQL o di un utente di finestra deve essere aggiunto come utente con autorizzazioni appropriate, in ogni database in cui lo script Python esegue una qualsiasi di queste operazioni:
    + Recupero di dati
    + Scrittura o aggiornamento di dati
    + Creazione di nuovi oggetti, ad esempio tabelle o stored procedure

Dopo che l'account di accesso o l'account utente di Windows è stato eseguito il provisioning e dispone delle autorizzazioni necessarie, è possibile eseguire il codice Python [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] utilizzando gli oggetti origine dati forniti dal **revoscalepy** libreria, o chiamando una stored stored procedure che contiene lo script Python.

Ogni volta che viene avviato uno script Python [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], la sicurezza del motore di database Ottiene il contesto di sicurezza dell'utente che ha avviato il processo e gestisce i mapping dell'utente o account di accesso agli oggetti a protezione diretta.

Pertanto, tutti gli script Python avviate da un client remoto è necessario specificare le informazioni di account di accesso o utente come parte della stringa di connessione.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interazione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] protezione e finestra di avvio

Quando uno script Python viene eseguito nel contesto del [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer, il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio Ottiene un account di lavoro disponibili (un account utente locale) da un pool di account di lavoro stabilito per i processi esterni e Usa l'account di lavoro a eseguire le attività correlate.

Si supponga, ad esempio, che si avvia uno script Python con le credenziali di dominio di Windows. Ottiene le credenziali di SQL Server e associa l'attività a un account di lavoro di finestra di avvio disponibile, ad esempio *SQLRUser01*.

> [!NOTE]
> Il nome del gruppo di account di lavoro è lo stesso indipendentemente dal fatto che si utilizzi R o Python. Tuttavia, viene creato un gruppo separato per ogni istanza in cui attiva qualsiasi linguaggio esterno.

Dopo il mapping a un account di lavoro, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] crea un token utente usato per avviare i processi. 

Dopo il completamento di tutte le operazioni di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], l'account utente di lavoro viene contrassegnato come libero e restituito al pool.

Per ulteriori informazioni su [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], vedere [componenti di SQL Server per supportare l'integrazione di Python](../../advanced-analytics/python/new-components-in-sql-server-to-support-python-integration.md).

### <a name="implied-authentication"></a>Autenticazione implicita

**L'autenticazione implicita** è il termine utilizzato per il processo in cui SQL Server Ottiene l'utente le credenziali e quindi esegue tutte le attività dello script esterno per conto di utenti, presupponendo che l'utente dispone delle autorizzazioni corrette nel database. L'autenticazione implicita è particolarmente importante se lo script Python deve effettuare una chiamata ODBC all'esterno del database di SQL Server. Ad esempio, il codice potrebbe recuperare un elenco più breve dei fattori da un foglio di calcolo o un'altra origine.

Per tali chiamate loopback abbia esito positivo, il gruppo che contiene gli account di lavoro, SQLRUserGroup, deve disporre delle autorizzazioni "Consenti accesso locale". Per impostazione predefinita, questo diritto viene assegnato a tutti i nuovi utenti locali, ma in alcune organizzazioni potrebbero essere applicati criteri di gruppo più restrittivo.

![Autenticazione implicita per R](media/implied-auth-python2.png)

## <a name="security-of-worker-accounts"></a>Protezione degli account di lavoro

Il mapping di un utente esterno di Windows o un account di accesso SQL valido a un account di lavoro è valido solo per la durata dell'istruzione SQL stored procedure che esegue lo script Python.

Le query parallele dallo stesso account di accesso sono mappate allo stesso account utente di lavoro.

La directory utilizzata per i processi vengono gestite dal [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], e directory sono accesso limitato. Per Python, PythonLauncher esegue questa attività. Ogni account di lavoro singole è limitato alla propria cartella e non è possibile accedere ai file nelle cartelle di livello superiore del relativo livello. Tuttavia, l'account di lavoro può leggere, scrivere o eliminare gli elementi figlio sotto la cartella di lavoro di sessione che è stato creato.

Per ulteriori informazioni su come modificare il numero di account di lavoro, i nomi di account o le password degli account, vedere [modificare il pool di account utente per l'apprendimento automatico di SQL Server](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).


## <a name="security-isolation-for-multiple-external-scripts"></a>Isolamento di sicurezza per più script esterni

Il meccanismo di isolamento si basa sugli account utente fisico. Quando vengono avviati i processi satellite per il runtime di un linguaggio specifico, ogni attività satellite usa l'account di lavoro specificato da [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Se un'attività richiede più satelliti, ad esempio nel caso di query parallele, viene usato un singolo account di lavoro per tutte le attività correlate.

Nessun account di lavoro può vedere o modificare i file usati da altri account di lavoro.

Un amministratore del computer può visualizzare le directory create per ogni processo. Ogni directory è identificata dal relativo GUID di sessione.

## <a name="see-also"></a>Vedere anche

[Panoramica dell'architettura](../../advanced-analytics/python/architecture-overview-sql-server-python.md)
