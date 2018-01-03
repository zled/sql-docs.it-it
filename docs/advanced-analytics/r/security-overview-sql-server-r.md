---
title: Sicurezza per SQL Server machine learning e R | Documenti Microsoft
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: "9"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dba0ea904e9b22cb99e4e0deb9befc32dd9e1abe
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2017
---
# <a name="security-for-sql-server-machine-learning-and-r"></a>Sicurezza per SQL Server machine learning e R

Questo articolo vengono descritti l'architettura di sicurezza globale che viene utilizzato per connettere il [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] dal database e i componenti correlati al runtime di R. Vengono forniti esempi del processo di protezione per questi scenari comuni per l'uso di R in un ambiente aziendale:

+ Esecuzione di funzioni RevoScaleR in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] da un client di data science
+ Esecuzione di R direttamente da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] usando stored procedure

## <a name="security-overview"></a>Cenni preliminari sulla sicurezza

Oggetto [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] account di accesso o account utente di Windows è necessario per eseguire gli script R che utilizzano dati di SQL Server o che eseguono con SQL Server come contesto di calcolo. Questo requisito si applica a entrambe [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] e SQL Server 2017 [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)].

Identifica l'account di accesso o utente di *entità di sicurezza*, che potrebbe essere necessario più livelli di accesso, a seconda dei requisiti di script R:

+ Autorizzazione per accedere al database in cui R è abilitata
+ Autorizzazioni per leggere gli oggetti protetti, ad esempio tabelle di dati
+ La possibilità di scrivere i nuovi dati a una tabella, ad esempio un modello, o la valutazione di risultati
+ La possibilità di creare nuovi oggetti, ad esempio tabelle, stored procedure che utilizzano script R, o personalizzato funzioni che il processo di usare R
+ Il diritto di installare i nuovi pacchetti nel computer di SQL Server, o usare R pacchetti forniti a un gruppo di utenti. 

Pertanto, ogni persona che esegue il codice R usando [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] come l'esecuzione del contesto deve essere mappato a un account di accesso nel database. Protezione di SQL Server, è in genere più semplice creare i ruoli per gestire i set di autorizzazioni e assegnare utenti a tali ruoli, anziché impostare singolarmente le autorizzazioni utente. 

Ad esempio, si supponga che è stato creato codice R che viene eseguito in un computer portatile, e si desidera eseguire il codice di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. È possibile farlo solo se vengono soddisfatte queste condizioni:

+ Il database consente le connessioni remote.
+ Un account di accesso SQL con il nome e la password usati nel codice R è stato aggiunto a [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] a livello di istanza. In alternativa, se si usa l'autenticazione integrata di Windows, l'utente di Windows specificato nella stringa di connessione deve essere aggiunto come utente nell'istanza.
+ L'account di accesso SQL o di un utente di Windows è necessario disporre dell'autorizzazione per l'esecuzione di script esterni. In genere, questa autorizzazione può essere aggiunta solo da un amministratore del database.
+ L'account di accesso SQL o l'utente di Windows deve essere aggiunto come utente, con le autorizzazioni appropriate, in ogni database in cui il processo R esegue una qualsiasi di queste operazioni:
    + Recupero di dati
    + Scrittura o aggiornamento di dati 
    + Creazione di nuovi oggetti, ad esempio tabelle o stored procedure

Dopo l'accesso o un account utente di Windows è stato eseguito il provisioning e dispone delle autorizzazioni necessarie, è possibile eseguire codice R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] utilizzando un oggetto di origine di dati R o chiamando una stored procedure. Ogni volta che viene avviata R [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], la sicurezza del motore di database Ottiene il contesto di sicurezza dell'utente che ha avviato il processo R o è stata eseguita la stored procedure e gestisce i mapping dell'utente o account di accesso agli oggetti a protezione diretta. 

Di conseguenza, tutti i processi R avviate da un client remoto è necessario specificare le informazioni di account di accesso o utente come parte della stringa di connessione.

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interazione di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] protezione e finestra di avvio

Quando uno script R viene eseguito nel contesto del computer [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], il servizio [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] ottiene un account di lavoro disponibile (un account utente locale) da un pool di account di lavoro creato per i processi esterni e usa tale account di lavoro per eseguire le attività correlate. 

Se, ad esempio, si avvia un processo R con le credenziali di dominio di Windows, l'account potrebbe essere mappato all'account di lavoro di Launchpad *SQLRUser01*.

Dopo il mapping a un account di lavoro, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] crea un token utente usato per avviare i processi. 

Dopo il completamento di tutte le operazioni di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], l'account utente di lavoro viene contrassegnato come libero e restituito al pool.

Per ulteriori informazioni su [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], vedere [componenti di SQL Server per supportare l'integrazione di R](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md).

### <a name="implied-authentication"></a>Autenticazione implicita

**L'autenticazione implicita** è il termine utilizzato per il processo in cui SQL Server Ottiene l'utente le credenziali e quindi esegue tutte le attività dello script esterno per conto di utenti, presupponendo che l'utente dispone delle autorizzazioni corrette nel database. L'autenticazione implicita è particolarmente importante se lo script R deve effettuare una chiamata ODBC all'esterno del database di SQL Server. Ad esempio, il codice potrebbe recuperare un elenco più breve dei fattori da un foglio di calcolo o un'altra origine.

Per tali chiamate loopback abbia esito positivo, il gruppo che contiene gli account di lavoro, SQLRUserGroup, deve disporre delle autorizzazioni "Consenti accesso locale". Per impostazione predefinita, questo diritto viene assegnato a tutti i nuovi utenti locali, ma in alcune organizzazioni potrebbero essere applicati criteri di gruppo più restrittivo.

![Autenticazione implicita per R](media/implied-auth-rsql.png)

## <a name="security-of-worker-accounts"></a>Protezione degli account di lavoro

Il mapping di un utente esterno di Windows o un account di accesso SQL valido a un account di lavoro è valido solo per la durata della durata della query SQL che esegue lo script R.

Le query parallele dallo stesso account di accesso sono mappate allo stesso account utente di lavoro.

Le directory usate per i processi sono gestite da [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] con RLauncher e prevedono restrizioni per l'accesso. L'account di lavoro non può accedere ai file nelle cartelle sopra la propria, ma può leggere, scrivere o eliminare gli elementi figlio nella cartella di lavoro della sessione creata per la query SQL con lo script R.

Per ulteriori informazioni su come modificare il numero di account di lavoro, i nomi di account o le password degli account, vedere [modificare il pool di account utente per l'apprendimento automatico di SQL Server](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md).

## <a name="security-isolation-for-multiple-external-scripts"></a>Isolamento di sicurezza per più script esterni

Il meccanismo di isolamento si basa sugli account utente fisici. Quando vengono avviati i processi satellite per il runtime di un linguaggio specifico, ogni attività satellite usa l'account di lavoro specificato da [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Se un'attività richiede più satelliti, ad esempio nel caso di query parallele, viene usato un singolo account di lavoro per tutte le attività correlate.

Nessun account di lavoro può vedere o modificare i file usati da altri account di lavoro.
 
Un amministratore del computer può visualizzare le directory create per ogni processo. Ogni directory è identificata dal relativo GUID di sessione.

## <a name="see-also"></a>Vedere anche

[Panoramica dell'architettura per l'apprendimento automatico di SQL Server](../../advanced-analytics/r/architecture-overview-sql-server-r.md)
