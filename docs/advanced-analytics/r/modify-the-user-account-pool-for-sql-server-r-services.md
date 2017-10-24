---
title: Modificare il pool di account utente per SQL Server R Services | Microsoft Docs
ms.custom:
- SQL2016_New_Updated
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b79170-5731-46b5-af8c-21164d28f3b0
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 33e22f7edec807d046798d89a9cd5daa642e8d3b
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="modify-the-user-account-pool-for-sql-server-r-services"></a>Modificare il pool di account utente per SQL Server R Services
  Come parte del processo di installazione di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], viene creato un nuovo *pool di account utente* Windows per supportare l'esecuzione delle attività tramite il servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]. Lo scopo di questi account di lavoro è quello di isolare l'esecuzione simultanea di script R da parte di utenti SQL diversi. 

Questo argomento descrive la configurazione predefinita, la sicurezza e la capacità per gli account di lavoro, nonché come modificare la configurazione predefinita.

## <a name="worker-accounts-used-by-r-services"></a>Account di lavoro usati da R Services   

Il gruppo di account Windows viene creato dall'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per ogni istanza in cui viene installato R Services. Se quindi sono installate più istanze che supportano R, ci saranno più gruppi di utenti.

-   In un'istanza predefinita il nome del gruppo è **SQLRUserGroup**. 
-   In un'istanza denominata il nome predefinito del gruppo ha un suffisso con il nome dell'istanza: ad esempio, **SQLRUserGroupNomeIstanza**. 

Per impostazione predefinita, il pool di account utente contiene 20 account utente. Nella maggior parte dei casi, 20 account sono più che sufficienti per supportare le sessioni di R, ma è possibile modificare il numero di account.
-  In un'istanza predefinita i singoli account sono denominati da **MSSQLSERVER01** a **MSSQLSERVER20**.  
-   Per un'istanza denominata il nome dei singoli account dipende dal nome dell'istanza: ad esempio da **NomeIstanza01** a **NomeIstanza20**.  

### <a name = "HowToChangeGroup"> </a>Come modificare il numero di account di lavoro R

Per modificare il numero di utenti nel pool di account, è necessario modificare le proprietà del servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], come descritto di seguito.  
  
Le password associate a ciascun account utente vengono generate in modo casuale, ma è possibile modificarle in un secondo momento, dopo la creazione degli account.  
  
1. Aprire Gestione configurazione SQL Server e selezionare **Servizi di SQL Server**.
2. Fare doppio clic sul servizio Launchpad di SQL Server e arrestare il servizio, se è in esecuzione. 
3.  Nella scheda **Servizio** verificare che la modalità di avvio sia impostata come automatica. Gli script R avranno esito negativo se Launchpad non è in esecuzione.
4.  Fare clic sulla scheda **Avanzate** e modificare il valore di **Conteggio degli utenti esterni**, se necessario. Questa impostazione controlla il numero di utenti di SQL diversi che possono eseguire query simultaneamente in R. Il valore predefinito è 20 account.
5. Facoltativamente, è possibile impostare l'opzione **Reimposta password utenti esterni** su _Sì_ se l'organizzazione ha criteri che richiedono la modifica delle password a intervalli regolari. In questo modo, le password crittografate gestite da Launchpad per gli account utente verranno rigenerate. Per altre informazioni, vedere [Applicazione dei criteri delle password](#bkmk_EnforcePolicy).    
6.  Riavviare il servizio.  

## <a name="managing-r-workload"></a>Gestione del carico di lavoro R

Il numero di account in questo pool determina il numero di sessioni R che possono essere attive simultaneamente.  Per impostazione predefinita, vengono creati 20 account, quindi 20 utenti diversi possono avere sessioni R attive simultaneamente. Se si prevede che sarà necessario consentire un maggior numero di utenti simultanei che eseguono script R, è possibile aumentare il numero di account di lavoro. 

Quando lo stesso utente esegue simultaneamente più script R, tutte le sessioni eseguite da tale utente useranno lo stesso account di lavoro. Un singolo utente può ad esempio eseguire 100 script R diversi simultaneamente, purché le risorse lo consentano, usando un singolo account di lavoro.

Il numero di account di lavoro che è possibile supportare e il numero di sessioni di R simultanee che un singolo utente può eseguire sono limitati solo dalle risorse del server.  In genere, la memoria rappresenta il primo collo di bottiglia che si incontra quando si usa il runtime di R.

In R Services le risorse che possono essere usate dagli script R sono controllate da SQL Server. È consigliabile monitorare l'utilizzo delle risorse mediante DMV di SQL Server o esaminare i contatori delle prestazioni sull'oggetto processo di Windows associato e modificare di conseguenza l'utilizzo della memoria del server. 
 
Se si ha SQL Server Enterprise Edition, è possibile allocare le risorse usate per l'esecuzione di script R configurando un [pool di risorse esterne](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md). 

Per altre informazioni sulla gestione della capacità degli script R, vedere questi articoli:

- [Configurazione di SQL Server (R Services)](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
-  [Case study sulle prestazioni (R Services)](../../advanced-analytics/r-services/performance-case-study-r-services.md)

## <a name="security"></a>Security

Ogni gruppo di utenti è associato al servizio [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] in un'istanza specifica e non può supportare i processi R eseguiti in altre istanze.

Per ogni account di lavoro, mentre la sessione è attiva, viene creata una cartella temporanea per archiviare gli oggetti script, i risultati intermedi e altre informazioni che R e SQL Server usano durante l'esecuzione degli script R. Questi file di lavoro, che si trovano nella cartella ExtensibilityData, sono accessibili solo dagli amministratori e vengono eliminati da SQL Server dopo il completamento dello script. 

Per altre informazioni, vedere [Panoramica della sicurezza](../../advanced-analytics/r-services/security-overview-sql-server-r.md).

### <a name="bkmk_EnforcePolicy"></a>Applicazione dei criteri delle password

Se l'organizzazione ha criteri che richiedono la modifica delle password a intervalli regolari, potrebbe essere necessario forzare il servizio Launchpad in modo da rigenerare le password crittografate gestite dal servizio per gli account di lavoro.  

Per abilitare questa impostazione e forzare l'aggiornamento delle password, aprire il riquadro **Proprietà** per il servizio Launchpad in Gestione configurazione SQL Server, fare clic su **Avanzate** e modificare l'impostazione di **Reimposta password utenti esterni** scegliendo **Sì**. Quando si applica questa modifica, le password vengono rigenerate immediatamente per tutti gli account utente. Per usare lo script R dopo questa modifica, è necessario riavviare il servizio Launchpad, che rileggerà quindi le password appena generate. 

Per reimpostare le password a intervalli regolari, è possibile impostare questo flag manualmente o usare uno script.

### <a name="additional-permission-required-to-support-remote-compute-contexts"></a>Autorizzazioni aggiuntive necessarie per supportare i contesti di elaborazione remota

Per impostazione predefinita, il gruppo di account di lavoro R **non** ha le autorizzazioni di accesso per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui è associato. Questo può costituire un problema se gli utenti R si connettono a SQL Server da un client remoto per eseguire script R oppure se uno script usa ODBC per ottenere dati aggiuntivi. 

Per garantire il supporto di questi scenari, l'amministratore del database deve fornire al gruppo di account di lavoro R le autorizzazioni di accesso all'istanza di SQL Server in cui verranno eseguiti gli script R (autorizzazioni **Connetti a**). In questo caso si parla di *autenticazione implicita*, che consente a SQL Server di eseguire gli script R usando le credenziali dell'utente remoto.

> [!NOTE]
> Questa limitazione non si applica se si usano account di accesso SQL per eseguire script R da una workstation remota, perché le credenziali di accesso SQL vengono passate in modo esplicito dal client R all'istanza di SQL Server e quindi a ODBC.


### <a name="how-to-enable-implied-authentication"></a>Come abilitare l'autenticazione implicita

1. Aprire SQL Server Management Studio come amministratore dell'istanza in cui si eseguirà il codice R.

2. Eseguire lo script seguente. Assicurarsi di modificare il nome del gruppo di utenti, se è stato cambiato quello predefinito, oltre che i nomi del computer e dell'istanza.

    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\SQLRUserGroup] FROM WINDOWS WITH DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO  
    ````


  
## <a name="see-also"></a>Vedere anche  
 [Configurazione (SQL Server R Services)](../../advanced-analytics/r-services/configuration-sql-server-r-services.md)
  

