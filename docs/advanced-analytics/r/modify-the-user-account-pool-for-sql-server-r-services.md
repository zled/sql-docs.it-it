---
title: Modificare il pool di account utente per l'apprendimento automatico di SQL Server | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 77b84e3117b0a1366f3d0b5f9d74802d938bc86b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31203443"
---
# <a name="modify-the-user-account-pool-for-sql-server-machine-learning"></a>Modificare il pool di account utente per l'apprendimento automatico di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Come parte del processo di installazione di [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)], viene creato un nuovo *pool di account utente* Windows per supportare l'esecuzione delle attività tramite il servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]. Lo scopo di questi account di lavoro è per isolare l'esecuzione simultanea di script esterni da utenti diversi di SQL.

Questo articolo descrive la configurazione predefinita, sicurezza e la capacità per gli account di lavoro e come modificare la configurazione predefinita.

**Si applica a:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)], [!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

## <a name="worker-accounts-used-for-external-script-execution"></a>Account di lavoro usati per l'esecuzione dello script esterno

Il gruppo di account Windows viene creato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione per ogni istanza del computer in cui è installato e abilitato apprendimento.

-   In un'istanza predefinita il nome del gruppo è **SQLRUserGroup**. Il nome è lo stesso, se si usa R, Python o entrambi.
-   In un'istanza denominata il nome predefinito del gruppo ha un suffisso con il nome dell'istanza: ad esempio, **SQLRUserGroupNomeIstanza**.

Per impostazione predefinita, il pool di account utente contiene 20 account utente. Nella maggior parte dei casi, è più che sufficiente per supportare l'attività di machine learning 20, ma è possibile modificare il numero di account. Il numero massimo di account è 100.
-  In un'istanza predefinita i singoli account sono denominati da **MSSQLSERVER01** a **MSSQLSERVER20**.
-   Per un'istanza denominata il nome dei singoli account dipende dal nome dell'istanza: ad esempio da **NomeIstanza01** a **NomeIstanza20**.

Se più di un'istanza Usa il machine learning, il computer sarà necessario più gruppi di utenti. Un gruppo non può essere condivisa tra più istanze.

### <a name = "HowToChangeGroup"> </a>Come modificare il numero di account di lavoro

Per modificare il numero di utenti nel pool di account, è necessario modificare le proprietà del servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], come descritto di seguito.

Le password associate a ciascun account utente vengono generate in modo casuale, ma è possibile modificarle in un secondo momento, dopo la creazione degli account.

1. Aprire Gestione configurazione SQL Server e selezionare **Servizi di SQL Server**.
2. Fare doppio clic sul servizio Launchpad di SQL Server e arrestare il servizio, se è in esecuzione.
3.  Nella scheda **Servizio** verificare che la modalità di avvio sia impostata come automatica. Quando la finestra di avvio non è in esecuzione, non è possibile avviare script esterni.
4.  Fare clic sulla scheda **Avanzate** e modificare il valore di **Conteggio degli utenti esterni**, se necessario. Questa impostazione determina il numero di utenti SQL diverso possibile eseguire script esterno sessioni contemporaneamente. Il valore predefinito è 20 account. Il numero massimo di utenti è 100.
5. Facoltativamente, è possibile impostare l'opzione **Reimposta password utenti esterni** su _Sì_ se l'organizzazione ha criteri che richiedono la modifica delle password a intervalli regolari. In questo modo, le password crittografate gestite da Launchpad per gli account utente verranno rigenerate. Per altre informazioni, vedere [Applicazione dei criteri delle password](#bkmk_EnforcePolicy).
6.  Riavviare il servizio Launchpad.

## <a name="managing-machine-learning-workloads"></a>Gestione dei carichi di lavoro di machine learning

Il numero di account in questo pool determina il numero di sessioni dello script esterno può essere attivo contemporaneamente.  Per impostazione predefinita, vengono creati 20 account, vale a dire che 20 diversi utenti possono avere R o Python sessioni attive in una sola volta. È possibile aumentare il numero di account di lavoro, se si prevede di eseguire script simultanea di più di 20.

Quando l'utente stesso esegue contemporaneamente più script esterni, tutte le sessioni eseguita da tale utente utilizzare lo stesso account di lavoro. Ad esempio, un singolo utente potrebbe essere 100 script R diverso in esecuzione contemporaneamente, purché consentono di risorse, ma tutti gli script verrebbero eseguito utilizzando un account di lavoro singola.

Il numero di account di lavoro che è possibile supportare e il numero di sessioni simultanee che è possibile eseguire qualsiasi singolo utente, è limitato solo dalle risorse del server. In genere, la memoria rappresenta il primo collo di bottiglia che si incontra quando si usa il runtime di R.

Le risorse utilizzate dagli script Python o R vengono gestite da SQL Server. È consigliabile monitorare l'utilizzo delle risorse mediante DMV di SQL Server o esaminare i contatori delle prestazioni sull'oggetto processo di Windows associato e modificare di conseguenza l'utilizzo della memoria del server. Se si dispone di SQL Server Enterprise Edition, è possibile allocare le risorse utilizzate per l'esecuzione di script esterni tramite la configurazione di un [pool di risorse esterne](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md).

Per ulteriori informazioni sulla gestione di machine learning capacità di attività, vedere gli articoli:

- [Configurazione di SQL Server per R Services](../../advanced-analytics/r/sql-server-configuration-r-services.md)
-  [Case study di prestazioni per R Services](../../advanced-analytics/r/performance-case-study-r-services.md)

## <a name="security"></a>Sicurezza

Ogni gruppo di utenti è associato al servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] in un'istanza specifica e non può supportare i processi R eseguiti in altre istanze.

Per ogni account di lavoro, mentre la sessione è attiva, viene creata una cartella temporanea per archiviare gli oggetti script, i risultati intermedi e altre informazioni che R e SQL Server usano durante l'esecuzione degli script R. Questi file di lavoro, che si trovano nella cartella ExtensibilityData, sono accessibili solo dagli amministratori e vengono eliminati da SQL Server dopo il completamento dello script. 

Per altre informazioni, vedere [Panoramica della sicurezza](../../advanced-analytics/r-services/security-overview-sql-server-r.md).

### <a name="bkmk_EnforcePolicy"></a>Applicazione dei criteri delle password

Se l'organizzazione ha criteri che richiedono la modifica delle password a intervalli regolari, potrebbe essere necessario forzare il servizio Launchpad in modo da rigenerare le password crittografate gestite dal servizio per gli account di lavoro.  

Per abilitare questa impostazione e forzare l'aggiornamento delle password, aprire il riquadro **Proprietà** per il servizio Launchpad in Gestione configurazione SQL Server, fare clic su **Avanzate** e modificare l'impostazione di **Reimposta password utenti esterni** scegliendo **Sì**. Quando si applica questa modifica, le password vengono rigenerate immediatamente per tutti gli account utente. Per usare lo script R dopo questa modifica, è necessario riavviare il servizio Launchpad, che rileggerà quindi le password appena generate. 

Per reimpostare le password a intervalli regolari, è possibile impostare questo flag manualmente o usare uno script.

### <a name="additional-permission-required-to-support-remote-compute-contexts"></a>Autorizzazioni aggiuntive necessarie per supportare i contesti di elaborazione remota

Per impostazione predefinita, il gruppo di account di lavoro R **non** ha le autorizzazioni di accesso per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui è associato. Questo può costituire un problema se gli utenti R si connettono a SQL Server da un client remoto per eseguire script R oppure se uno script usa ODBC per ottenere dati aggiuntivi. 

Per garantire il supporto di questi scenari, l'amministratore del database deve fornire al gruppo di account di lavoro R le autorizzazioni di accesso all'istanza di SQL Server in cui verranno eseguiti gli script R (autorizzazioni **Connetti a**). Ciò è detto *autenticazione implicita*e consente di eseguire gli script R usando le credenziali dell'utente remoto di SQL Server.

> [!NOTE]
> Questa limitazione non si applica se si usano account di accesso SQL per eseguire script R da una workstation remota, perché le credenziali di accesso SQL vengono passate in modo esplicito dal client R all'istanza di SQL Server e quindi a ODBC.


### <a name="how-to-enable-implied-authentication"></a>Come abilitare l'autenticazione implicita

1. Aprire SQL Server Management Studio come amministratore nell'istanza in cui si eseguirà il codice R o Python.

2. Eseguire lo script seguente. Assicurarsi di modificare il nome del gruppo di utenti, se è stato cambiato quello predefinito, oltre che i nomi del computer e dell'istanza.

    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\SQLRUserGroup] FROM WINDOWS WITH DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ````

