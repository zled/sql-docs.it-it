---
title: Panoramica della sicurezza per Python in SQL Server Machine Learning | Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: a33701283635327fcaac4a9629cb02044b30dda8
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890057"
---
# <a name="security-overview-for-python-in-sql-server-machine-learning"></a>Panoramica della sicurezza per Python in SQL Server Machine Learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo argomento viene descritta l'architettura di sicurezza che consente di connettere il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] dal database e i componenti Python. Vengono forniti esempi del processo di sicurezza per due scenari comuni: esecuzione di Python in SQL Server utilizzando una stored procedure e l'esecuzione di Python con SQL Server come contesto di calcolo remoto.

## <a name="security-overview"></a>Panoramica della sicurezza

Oggetto [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] account utente di Windows o account di accesso serve all'esecuzione di script Python in SQL Server. Questi *le entità di sicurezza* vengono gestiti a livello di istanza e database e identificare gli utenti che dispongono dell'autorizzazione per connettersi al database, leggere e scrivere i dati o creare oggetti di database, ad esempio tabelle o stored procedure. Inoltre, gli utenti che eseguono lo script Python devono avere l'autorizzazione per eseguire script esterni a livello di database.

Anche gli utenti che usano Python in uno strumento esterno devono essere mappati a un account di accesso o un account nel database se l'utente dovrà eseguire Python code in-database, o accedere agli oggetti di database e i dati. Se lo script Python viene inviato da un client di analisi scientifica dei dati remota o all'uso di una procedura T-SQL archiviate, sono necessarie le stesse autorizzazioni.

Si supponga, ad esempio, che è stato creato uno script Python eseguito sul computer portatile e si desidera eseguire il codice in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. È necessario assicurarsi che siano soddisfatte le condizioni seguenti:

+ Il database consente le connessioni remote.
+ L'account di accesso SQL o l'account di Windows utilizzato per l'accesso al database è stato aggiunto il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] a livello di istanza.
+ È necessario concedere all'account di accesso SQL o all'utente di Windows l'autorizzazione per eseguire gli script esterni. In genere, questa autorizzazione può essere aggiunta solo da un amministratore del database.
+ L'account di accesso SQL o un utente di Windows deve essere aggiunto come utente, con le autorizzazioni appropriate, in ogni database in cui lo script Python esegue una qualsiasi di queste operazioni:
    + Recupero di dati
    + Scrittura o aggiornamento di dati
    + Creazione di nuovi oggetti, ad esempio tabelle o stored procedure

Dopo che l'account di accesso o l'account utente di Windows è stato effettuato il provisioning e le autorizzazioni necessarie, è possibile eseguire il codice Python [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] utilizzando gli oggetti origine dei dati forniti dal **revoscalepy** library, o chiamando una stored procedure che contiene lo script Python.

Ogni volta che viene avviato uno script Python da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], la sicurezza del motore di database Ottiene il contesto di sicurezza dell'utente che ha avviato il processo e gestisce i mapping dell'utente o account di accesso agli oggetti a protezione diretta.

Pertanto, tutti gli script Python che vengono avviati da un client remoto devono specificare le informazioni sull'account di accesso o utente come parte della stringa di connessione.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interazione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] sicurezza e la sicurezza di Launchpad

Quando viene eseguito uno script di Python nel contesto del [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] computer, il [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio Ottiene un account di lavoro disponibile (un account utente locale) da un pool di account di lavoro stabilito per i processi esterni e Usa l'account di lavoro a eseguire le attività correlate.

Si supponga, ad esempio, che si avvia uno script Python con le credenziali di dominio di Windows. Ottiene le credenziali di SQL Server e associa l'attività a un account di lavoro Launchpad disponibile, ad esempio *SQLRUser01*.

> [!NOTE]
> Il nome del gruppo di account di lavoro è la stessa indipendentemente dal fatto che si usa R o Python. Tuttavia, viene creato un gruppo separato per ogni istanza in cui si abilita qualsiasi linguaggio esterno.

Dopo il mapping a un account di lavoro, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] crea un token utente usato per avviare i processi. 

Dopo il completamento di tutte le operazioni di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], l'account utente di lavoro viene contrassegnato come libero e restituito al pool.

Per altre informazioni sul servizio, vedere [framework di estendibilità](../concepts/extensibility-framework.md).

### <a name="implied-authentication"></a>Autenticazione implicita

**L'autenticazione implicita** è il termine usato per il processo in cui SQL Server Ottiene l'utente le credenziali e quindi esegue tutte le attività di script esterni per conto di utenti, presupponendo che l'utente dispone delle autorizzazioni corrette nel database. L'autenticazione implicita è particolarmente importante se lo script Python deve effettuare una chiamata ODBC all'esterno del database di SQL Server. Ad esempio, il codice potrebbe recuperare un elenco più breve di fattori da un foglio di calcolo o un'altra origine.

Per tali chiamate loopback abbia esito positivo, il gruppo che contiene gli account di lavoro, SQLRUserGroup, deve avere le autorizzazioni "Consenti accesso locale". Per impostazione predefinita, questo diritto viene assegnato a tutti i nuovi utenti locali, ma in alcune organizzazioni potrebbero essere applicati criteri di gruppo più rigorosi.

![Autenticazione implicita per R](media/implied-auth-python2.png)

## <a name="security-of-worker-accounts"></a>Sicurezza dell'account di lavoro

Il mapping di un utente esterno di Windows o un account di accesso SQL valido per un account di lavoro è valido solo per la durata del SQL stored procedure che esegue lo script Python.

Le query parallele dallo stesso account di accesso sono mappate allo stesso account utente di lavoro.

Le directory usate per i processi gestite dal [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], e le directory sono l'accesso limitato. Per Python, PythonLauncher esegue questa attività. Ogni account di lavoro singoli sarà limitato alla propria cartella e non può accedere ai file nelle cartelle sopra il proprio livello. Tuttavia, l'account di lavoro può leggere, scrivere o eliminare gli elementi figlio sotto la cartella di lavoro di sessione che è stato creato.

Per altre informazioni su come modificare il numero di account di lavoro, i nomi degli account o le password degli account, vedere [modificare il pool di account utente per l'apprendimento di SQL Server](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).


## <a name="security-isolation-for-multiple-external-scripts"></a>Isolamento di sicurezza per più script esterni

Il meccanismo di isolamento si basa sugli account utente fisici. Quando vengono avviati i processi satellite per il runtime di un linguaggio specifico, ogni attività satellite usa l'account di lavoro specificato da [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Se un'attività richiede più satelliti, ad esempio nel caso di query parallele, viene usato un singolo account di lavoro per tutte le attività correlate.

Nessun account di lavoro può vedere o modificare i file usati da altri account di lavoro.

Un amministratore del computer può visualizzare le directory create per ogni processo. Ogni directory è identificata dal relativo GUID di sessione.

## <a name="see-also"></a>Vedere anche

[Panoramica dell'architettura](../../advanced-analytics/python/architecture-overview-sql-server-python.md)
