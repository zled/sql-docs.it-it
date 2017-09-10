---
title: Panoramica della sicurezza (SQL Server R Services) | Microsoft Docs
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8fc84754-7fbf-4c1b-9150-7d88680b3e68
caps.latest.revision: 9
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8388d7c9d22a49a49a1a45a6fa6b479107f9ccae
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="security-overview-sql-server-r-services"></a>Panoramica della sicurezza (SQL Server R Services)

Questo argomento descrive l'architettura di sicurezza generale usata per connettere il motore di database di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e i componenti correlati al runtime R. Vengono forniti esempi del processo di sicurezza per due scenari comuni per l'uso di R in un ambiente aziendale:

+ Esecuzione di funzioni RevoScaleR in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] da un client di data science
+ Esecuzione di R direttamente da [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] usando stored procedure

## <a name="security-overview"></a>Panoramica della sicurezza

Oggetto [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] account di accesso o account utente di Windows è necessario per eseguire gli script R che utilizzano dati di SQL Server o che eseguono con SQL Server come contesto di calcolo. Questo requisito si applica sia [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] e servizi di SQL Server 2017 Machine Learning. 

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

## <a name="interaction-of-includessnoversionmdincludesssnoversion-mdmd-security-and-launchpad-security"></a>Interazione tra la sicurezza di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] e la sicurezza di LaunchPad

Quando uno script R viene eseguito nel contesto del computer [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], il servizio [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] ottiene un account di lavoro disponibile (un account utente locale) da un pool di account di lavoro creato per i processi esterni e usa tale account di lavoro per eseguire le attività correlate. 

Se, ad esempio, si avvia un processo R con le credenziali di dominio di Windows, l'account potrebbe essere mappato all'account di lavoro di Launchpad *SQLRUser01*.

Dopo il mapping a un account di lavoro, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] crea un token utente usato per avviare i processi. 

Dopo il completamento di tutte le operazioni di [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], l'account utente di lavoro viene contrassegnato come libero e restituito al pool.

Per altre informazioni su [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)], vedere [Nuovi componenti di SQL Server per il supporto di R Services](../../advanced-analytics/r-services/new-components-in-sql-server-to-support-r.md).

> [!NOTE]
Per consentire a Launchpad di gestire gli account di lavoro ed eseguire i processi R, il gruppo che contiene gli account di lavoro, SQLRUserGroup, deve disporre delle autorizzazioni "Consenti accesso locale", altrimenti R Services potrebbe non funzionare. Per impostazione predefinita, questo diritto viene assegnato a tutti i nuovi utenti locali, ma in alcune organizzazioni potrebbero essere in vigore criteri di gruppo più rigorosi, che impediscono la connessione degli account di lavoro a SQL Server per eseguire i processi R.  

## <a name="security-of-worker-accounts"></a>Sicurezza degli account di lavoro

Il mapping di un utente esterno di Windows o un account di accesso SQL valido a un account di lavoro è valido solo per la durata della durata della query SQL che esegue lo script R. 

Le query parallele dallo stesso account di accesso sono mappate allo stesso account utente di lavoro.

Le directory usate per i processi sono gestite da [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] con RLauncher e prevedono restrizioni per l'accesso. L'account di lavoro non può accedere ai file nelle cartelle sopra la propria, ma può leggere, scrivere o eliminare gli elementi figlio nella cartella di lavoro della sessione creata per la query SQL con lo script R.

Per altre informazioni su come modificare il numero di account di lavoro, i nomi degli account o le password degli account, vedere [Modificare il pool di account utente per SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).


## <a name="security-isolation-for-multiple-external-scripts"></a>Isolamento di sicurezza per più script esterni

Il meccanismo di isolamento si basa sugli account utente fisici. Quando vengono avviati i processi satellite per il runtime di un linguaggio specifico, ogni attività satellite usa l'account di lavoro specificato da [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Se un'attività richiede più satelliti, ad esempio nel caso di query parallele, viene usato un singolo account di lavoro per tutte le attività correlate.

Nessun account di lavoro può vedere o modificare i file usati da altri account di lavoro.
 
Un amministratore del computer può visualizzare le directory create per ogni processo. Ogni directory è identificata dal relativo GUID di sessione.

## <a name="see-also"></a>Vedere anche
[Panoramica dell'architettura](../../advanced-analytics/r-services/architecture-overview-sql-server-r.md)

