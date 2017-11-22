---
title: Controllo locale per la raccolta di dati relativi all'utilizzo di SQL Server | Microsoft Docs
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- dbe-security
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Local Audit
ms.assetid: a0665916-7789-4f94-9086-879275802cf3
caps.latest.revision: "8"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 48de69218e71bb9688e6d7a3d0669b43baefe150
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="local-audit-for-sql-server-usage-feedback-collection"></a>Controllo locale per la raccolta di dati relativi all'utilizzo di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
## <a name="introduction"></a>Introduzione

In Microsoft SQL Server sono disponibili funzionalità abilitate per Internet che sono in grado di raccogliere e inviare a Microsoft dati relativi al computer o al dispositivo ("dati standard sul computer"). Il componente per il controllo locale della [raccolta di dati relativi all'utilizzo di SQL Server](http://support.microsoft.com/kb/3153756) scrive i dati raccolti dal servizio in una specifica cartella, che rappresenta i dati (log) da inviare a Microsoft. Lo scopo del controllo locale è quello di consentire ai clienti di visualizzare tutti i dati che Microsoft raccoglie con questa funzionalità, per motivi di conformità alle normative o rispetto della privacy.  

In SQL Server 2016 CU2 il controllo locale è configurabile a livello di istanza per il motore di database di SQL Server ed SQL Server Analysis Services (SSAS). In SQL Server 2016 CU4 e SQL Server 2016 SP1 il controllo locale è abilitato anche per SQL Server Integration Services (SSIS). Per altri componenti di SQL Server installati durante la fase di installazione del programma e per strumenti di SQL Server scaricati o installati successivamente, la funzionalità di controllo locale per la raccolta dei dati relativi all'utilizzo non è disponibile. 

## <a name="prerequisites"></a>Prerequisiti 

Per abilitare il controllo locale in ogni istanza di SQL Server sono previsti i prerequisiti seguenti: 

1. L'istanza è stata aggiornata a SQL Server 2016 RTM CU2 o versione successiva. 

1. L'utente deve essere un amministratore di sistema o un ruolo con diritti di accesso per aggiungere e modificare la chiave del Registro di sistema, creare cartelle, gestire la sicurezza delle cartelle e arrestare o avviare un servizio di Windows.  

## <a name="pre-configuration-steps-prior-to-turning-on-local-audit"></a>Passaggi di configurazione preliminari all'abilitazione del controllo locale 

Prima di abilitare il controllo locale, un amministratore di sistema deve:

1. Conoscere il nome dell'istanza di SQL Server e l'account di accesso al servizio di telemetria di Analisi utilizzo software di SQL Server. 

1. Configurare una nuova cartella per i file del controllo locale.

1. Concedere le autorizzazioni all'account di accesso al servizio di telemetria di Analisi utilizzo software di SQL Server.

1. Creare un'impostazione della chiave del Registro di sistema per configurare la directory di destinazione della funzionalità di controllo locale. 

    Per il motore di database e Integration Services creare la chiave in *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL14.\<NOMEISTANZA\>\\CPE*. 
    
    Per Analysis Services creare la chiave in *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS14.\<NOMEISTANZA\>\\CPE*.

### <a name="get-the-sql-server-ceip-service-logon-account"></a>Ottenere l'account di accesso al servizio Analisi utilizzo software di SQL Server

Per ottenere l'account di accesso al servizio di telemetria di Analisi utilizzo software di SQL Server, seguire questa procedura:
 
1. Avviare **Servizi** facendo clic sul pulsante **Windows**  e digitando *services.msc*. 

2. Passare al servizio appropriato. Ad esempio, per il motore di database individuare **Servizio Analisi utilizzo software di SQL Server \<nome istanza\>**. Per Analysis Services individuare **Analisi utilizzo software di SQL Server Analysis Services \<nome istanza\>**. Per Integration Services individuare **SQL Server Integration Services CEIP servizio 13**.

3. Fare clic con il pulsante destro del mouse sul servizio e scegliere **Proprietà**. 

4. Fare clic sulla scheda **Accesso** . L'account di accesso è elencato in **Il seguente account**. 

### <a name="configure-a-new-folder-for-the-local-audit-files"></a>Configurare una nuova cartella per i file del controllo locale.    

Creare una nuova cartella (directory del controllo locale) in cui archiviare i log della funzionalità di controllo locale. Ad esempio, il percorso completo della directory del controllo locale per un'istanza predefinita del motore di database sarà: *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\*. 
 
> Nota: configurare il percorso di directory per il controllo locale all'esterno del percorso di installazione di SQL Server per evitare che la funzionalità di controllo e l'applicazione di patch causino problemi a SQL Server.

  ||Decisione di progettazione|Consiglio|  
  |------|-----------------|----------|  
  |![Casella di controllo](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Pianificare la disponibilità di spazio |Per un carico di lavoro moderato con circa 10 database, prevedere circa 2 MB di spazio su disco al giorno per ogni istanza.|  
|![Casella di controllo](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Definire directory separate | Creare una directory per ogni istanza. Ad esempio, usare *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\* per un'istanza di SQL Server denominata `MSSQLSERVER`. Ciò semplifica la gestione dei file.
|![Casella di controllo](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Definire cartelle separate |Usare una cartella specifica per ogni servizio. Ad esempio, per un determinato nome di istanza, specificare una singola cartella per il motore di database. Se un'istanza di SSAS usa lo stesso nome di istanza, creare una cartella separata per SSAS. Se per entrambe le istanze del motore di database e di Analysis Services è configurata la stessa cartella, tutti i dati del controllo locale provenienti da tali istanze verranno scritti nello stesso file di log.| 
|![Casella di controllo](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Casella di controllo")|Concedere le autorizzazioni all'account di accesso al servizio di telemetria di Analisi utilizzo software di SQL Server|Abilitare i diritti **Visualizzazione contenuto cartella**, **Lettura** e **Scrittura** per l'account di accesso del servizio di telemetria di Analisi utilizzo software di SQL Server.|


### <a name="grant-permissions-to-the-sql-server-ciep-telemetry-service-logon-account"></a>Concedere le autorizzazioni all'account di accesso al servizio di telemetria di Analisi utilizzo software di SQL Server
  
1. In **Esplora file**individuare la posizione della nuova cartella.  

1. Fare clic con il pulsante destro del mouse sulla nuova cartella e scegliere **Proprietà**. 

1. Nella scheda **Sicurezza**fare clic sull'autorizzazione di gestione **Modifica** .

1. Fare clic su **Aggiungi** e digitare le credenziali del servizio di telemetria di Analisi utilizzo software di Server SQL, ad esempio `NT Service\SQLTELEMETRY`.   

1. Fare clic su **Controlla nomi** per convalidare il nome specificato e quindi fare clic su **OK**. 

1. Nella finestra di dialogo **Autorizzazione** scegliere l'account di accesso al servizio di telemetria di Analisi utilizzo software di SQL Server e fare clic su **Visualizzazione contenuto cartella**, **Lettura** e **Scrittura**.  

1. Fare clic su **OK** per applicare immediatamente le modifiche alle autorizzazioni. 
  
### <a name="create-a-registry-key-setting-to-configure-local-audit-target-directory"></a>Creare un'impostazione della chiave del Registro di sistema per configurare la directory di destinazione della funzionalità di controllo locale.

1. Avviare regedit.  

1. Passare al percorso di CPE appropriato. 

    Per il motore di database e Integration Services usare *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL14.\<NOMEISTANZA\>\\CPE*. 
    
    Per Analysis Services usare *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS14.\<NOMEISTANZA\>\\CPE*.

1. Fare clic con il pulsante destro del mouse sul percorso di CPE e scegliere **Nuovo**. Fare clic su **Valore stringa**.

1. Denominare la nuova chiave del Registro di sistema `UserRequestedLocalAuditDirectory`. 
 
## <a name="turning-local-audit-on-or-off"></a>Abilitazione o disabilitazione del controllo locale

Dopo aver completato i passaggi di configurazione preliminari, è possibile abilitare il controllo locale. A tale scopo, usare un account di amministratore di sistema, o un ruolo simile con accesso alla modifica delle chiavi del Registro di sistema, per abilitare o disabilitare il controllo locale seguendo questa procedura. 

1. Avviare **regedit**.  

1. Passare al percorso di CPE appropriato. 

    Per il motore di database e Integration Services usare *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL14.\<NOMEISTANZA\>\\CPE*. 
    
    Per Analysis Services usare *HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS14.\<NOMEISTANZA\>\\CPE*.

1. Fare clic con il pulsante destro del mouse su **UserRequestedLocalAuditDirectory** e scegliere *Modifica*. 

1. Per abilitare il controllo locale, digitare il relativo percorso, ad esempio *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\*.
 
    Per disabilitare il controllo locale, svuotare il valore in **UserRequestedLocalAuditDirectory**.

1. Chiudere **regedit**. 

Analisi utilizzo software di SQL Server dovrebbe riconoscere immediatamente l'impostazione del controllo locale se il servizio è già in esecuzione. Per avviare il servizio Analisi utilizzo software di SQL Server, l'amministratore di sistema o un utente con diritti di accesso per avviare o arrestare Servizi Windows può seguire questa procedura: 

1. Avviare l'applicazione Servizi facendo clic sul pulsante Windows e digitando Servizi. 

1. Passare al servizio appropriato. 

    Per il motore di database usare **Servizio Analisi utilizzo software di SQL Server (\<NOMEISTANZA\>)**. 
    
    Per Analysis Services usare **Analisi utilizzo software di SQL Server Analysis Services (\<NOMEISTANZA\>)**. 

1. Fare clic con il pulsante destro del mouse sul servizio e scegliere Riavvia. 

1. Verificare che lo stato del servizio sia **In esecuzione**. 

La funzionalità di controllo locale genererà un file di log al giorno. Ai file di log viene assegnato un nome nel formato `<YYYY-MM-DD>.json`. Ad esempio, *2016-07-12.json*. Se nella directory designata esiste già un file per il giorno corrente, i dati verranno aggiunti a tale file. In caso contrario, ne verrà creato uno nuovo. 

> Nota: dopo l'abilitazione del controllo locale, possono trascorrere fino a 5 minuti prima che il file di log venga scritto per la prima volta. 

## <a name="maintenance"></a>Manutenzione 

1. Per limitare l'utilizzo di spazio su disco per i file scritti dalla funzionalità di controllo locale, configurare criteri o un processo regolare per rimuovere dalla directory del controllo locale i file meno recenti, non necessari.  

2. Proteggere il percorso della directory del controllo locale in modo che sia accessibile solo alle persone appropriate. Si noti che i file di log contengono informazioni come descritto in [Come configurare SQL Server 2016 per inviare commenti e suggerimenti a Microsoft](http://support.microsoft.com/kb/3153756). È quindi opportuno impostare diritti di accesso a questi file in modo da impedirne la lettura alla maggior parte dei membri dell'organizzazione.  

## <a name="data-dictionary-of-local-audit-output-data-structure"></a>Dizionario dei dati della struttura di dati di output del controllo locale 

- I file di log del controllo locale sono in formato JSON, contenente un set di oggetti (righe) che rappresentano i punti dati inviati a Microsoft nella data e all'ora definite da **emitTime**.  

- Ogni riga segue uno schema specifico identificato da **schemaVersion**.   

- Ogni riga corrisponde a un output di una sessione del servizio SQLCEIP identificata come **sessionID**.  

- Le righe vengono inviate in base a una sequenza identificata da **sequence**. 

- Ogni riga di punto dati contiene l'output di un elemento **queryIdentifier** che può essere una query T-SQL, una sessione XE o un messaggio correlato a un tipo di traccia, identificata come **traceName**.   

- Gli elementi**queryIdentifier** vengono riuniti in gruppi a cui viene assegnata una versione con **querySetVersion**. 

- L'elemento**data** contiene l'output dell'esecuzione di query corrispondente la cui durata è definita da **queryTimeInTicks**. 

- Gli elementi**queryIdentifier** per le query T-SQL contengono la definizione di query T-SQL archiviata nella query. 


| Gerarchia logica delle informazioni del controllo locale | Colonne correlate |
| ------ | -------|
| Intestazione | emitTime, schemaVersion 
| Computer | hostname, domainHash, sqmID, operatingSystem 
| Istanza | instanceName, correlationID, clientVersion 
| Sessione | sessionID, traceName 
| Query | sequence, querySetVersion, queryIdentifier, query, queryTimeInTicks 
| data |  data 

### <a name="namevalue-pairs-definition-and-examples"></a>Definizione di coppie nome/valore ed esempi 

Le colonne elencate di seguito rappresentano l'ordinamento dell'output dei file del controllo locale. Per rendere anonimi i valori per alcune delle colonne seguenti viene usato un hash unidirezionale con SHA 256.  

| Nome | Descrizione | Valori di esempio
|-------|--------| ----------|
|hostname | Nome (reso anonimo) del computer in cui è installato SQL Server| de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11 
|domainHash| Hash di dominio (reso anonimo) del computer che ospita l'istanza di SQL Server | de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11 
|sqmId |Identificatore che rappresenta il computer in cui è installato SQL Server | 02AF58F5-753A-429C-96CD-3900E90DB990 
|NOMEISTANZA| Nome (reso anonimo) dell'istanza di SQL Server| e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 
|schemaVersion| Versione dello schema di SQLCEIP |  3 
|emitTime |Data e ora di invio dei punti dati in UTC (Universal Time Coordinated) | 2016-09-08T17:20:22.1124269Z 
|sessionID | Identificatore di sessione del servizio SQLCEIP | 89decf9a-ad11-485c-94a7-fefb3a02ed86 
| correlationId | Segnaposto per un identificatore aggiuntivo | 0 
|sequence | Numero di sequenza dei punti dati inviati nel corso della sessione | 15 
| clientVersion | Versione dell'istanza di SQL Server | 13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223) 
| operatingSystem | Versione del sistema operativo in cui è installata l'istanza di SQL Server | Microsoft Windows Server 2012 R2 Datacenter 
| querySetVersion | Versione di un gruppo di definizioni di query | 1.0.0.0 
|traceName | Categorie di tracce: (SQLServerXeQueries, SQLServerPeriodicQueries, SQLServerOneSettingsException) | SQLServerPeriodicQueries 
|queryIdentifier | Identificatore della query | SQLServerProperties.002 
|data   | Output delle informazioni raccolte su queryIdentifier come output della query T-SQL, della sessione XE o dell'applicazione |   [{"Collation": "SQL_Latin1_General_CP1_CI_AS","SqlFTinstalled": "0" "SqlIntSec": "1","IsSingleUser": "0","SqlFilestreamMode": "0","SqlPbInstalled": "0","SqlPbNodeRole": "","SqlVersionMajor": "13","SqlVersionMinor": "0","SqlVersionBuild": "2161","ProductBuildType": "","ProductLevel": "RTM","ProductUpdateLevel": "CU2","ProductUpdateReference": "KB3182270","ProductRevision": "3","SQLEditionId": "-1534726760","IsClustered": "0","IsHadrEnabled": "0","SqlAdvAInstalled": "0","PacketReceived": "1210","Version": "Microsoft SQL Server 2016 (RTM-CU2) (KB3182270) - 13.0.2161.3 (X64) \n\tSep  7 2016 14:24:16 \n\tCopyright (c) Microsoft Corporation\n\tStandard Edition (64-bit) on Windows Server 2012 R2 Datacenter 6.3 \u003cX64\u003e (Build 9600: ) (Hypervisor)\n"}],
|Query| Se applicabile, definizione di query T-SQL correlata all'elemento queryIdentifier che genera i dati.        Questo componente non viene caricato dal servizio Analisi utilizzo software di SQL Server. È incluso nel controllo locale solo come riferimento per i clienti.| SELECT\n      SERVERPROPERTY(\u0027Collation\u0027) AS [Collation],\n      SERVERPROPERTY(\u0027IsFullTextInstalled\u0027) AS [SqlFTinstalled],\n      SERVERPROPERTY(\u0027IsIntegratedSecurityOnly\u0027) AS [SqlIntSec],\n      SERVERPROPERTY(\u0027IsSingleUser\u0027) AS [IsSingleUser],\n      SERVERPROPERTY (\u0027FileStreamEffectiveLevel\u0027) AS [SqlFilestreamMode],\n      SERVERPROPERTY(\u0027IsPolybaseInstalled\u0027) AS [SqlPbInstalled],\n      SERVERPROPERTY(\u0027PolybaseRole\u0027) AS [SqlPbNodeRole],\n      SERVERPROPERTY(\u0027ProductMajorVersion\u0027) AS [SqlVersionMajor],\n      SERVERPROPERTY(\u0027ProductMinorVersion\u0027) AS [SqlVersionMinor],\n      SERVERPROPERTY(\u0027ProductBuild\u0027) AS [SqlVersionBuild],\n      SERVERPROPERTY(\u0027ProductBuildType\u0027) AS ProductBuildType,\n      SERVERPROPERTY(\u0027ProductLevel\u0027) AS ProductLevel,\n      SERVERPROPERTY(\u0027ProductUpdateLevel\u0027) AS ProductUpdateLevel,\n      SERVERPROPERTY(\u0027ProductUpdateReference\u0027) AS ProductUpdateReference,\n      RIGHT(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)),CHARINDEX(\u0027.\u0027, REVERSE(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)))) - 1) AS ProductRevision,\n      SERVERPROPERTY(\u0027EditionID\u0027) AS SQLEditionId,\n      SERVERPROPERTY(\u0027IsClustered\u0027) AS IsClustered,\n      SERVERPROPERTY(\u0027IsHadrEnabled\u0027) AS IsHadrEnabled,\n      SERVERPROPERTY(\u0027IsAdvancedAnalyticsInstalled\u0027) AS [SqlAdvAInstalled],\n      @@PACK_RECEIVED AS PacketReceived,\n      @@VERSION AS Version
|queryTimeInTicks | Tempo impiegato per l'esecuzione della query con la categoria di traccia seguente: (SQLServerXeQueries, SQLServerPeriodicQueries) |  0 
 
### <a name="trace-categories"></a>Categorie di traccia 
Attualmente i dati vengono raccolti in base alle categorie di traccia seguenti: 

- **SQLServerXeQueries**: contiene i punti dati raccolti tramite la sessione di eventi estesi. 

- **SQLServerPeriodicQueries**: contiene i punti dati raccolti tramite query periodiche eseguite in un'istanza di SQL Server. 

- **SQLServerPerDBPeriodicQueries**: contiene i punti dati raccolti tramite query periodiche eseguite su un massimo di 30 database in un'istanza di SQL Server. 

- **SQLServerOneSettingsException**: contiene i messaggi di eccezione correlati all'aggiornamento dello schema e/o al set di query. 

- **DigitalProductID**: contiene i punti dati per l'aggregazione degli ID di prodotto digitale (resi anonimi) con hash (SHA-256) delle istanze di SQL Server. 

### <a name="local-audit-file-examples"></a>Esempi di file del controllo locale



Di seguito è riportato un estratto di un output di file JSON della funzionalità di controllo locale.

```JSON
{
    "hostName": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "domainHash": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "sqmId": "02AF58F5-753A-429C-96CD-3900E90DB990",
    "instanceName": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "schemaVersion": "3",
    "emitTime": "2016-09-08T17:20:22.1124269Z",
    "sessionId": "89decf9a-ad11-485c-94a7-fefb3a02ed86",
    "correlationId": 0,
    "sequence": 15,
    "clientVersion": "13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223)",
    "operatingSystem": "Microsoft Windows Server 2012 R2 Datacenter",
    "querySetVersion": "1.0.0.0",
    "traceName": "SQLServerPeriodicQueries",
    "queryIdentifier": "SQLServerProperties.002",
    "data": [
      {
        "Collation": "SQL_Latin1_General_CP1_CI_AS",
        "SqlFTinstalled": "0",
        "SqlIntSec": "1",
        "IsSingleUser": "0",
        "SqlFilestreamMode": "0",
        "SqlPbInstalled": "0",
        "SqlPbNodeRole": "",
        "SqlVersionMajor": "13",
        "SqlVersionMinor": "0",
        "SqlVersionBuild": "2161",
        "ProductBuildType": "",
        "ProductLevel": "RTM",
        "ProductUpdateLevel": "CU2",
        "ProductUpdateReference": "KB3182270",
        "ProductRevision": "3",
        "SQLEditionId": "-1534726760",
        "IsClustered": "0",
        "IsHadrEnabled": "0",
        "SqlAdvAInstalled": "0",
        "PacketReceived": "1210",
        "Version": "Microsoft SQL Server 2016 (RTM-CU2) (KB3182270) - 13.0.2161.3 (X64) \n\tSep  7 2016 14:24:16 \n\tCopyright (c) Microsoft Corporation\n\tStandard Edition (64-bit) on Windows Server 2012 R2 Datacenter 6.3 \u003cX64\u003e (Build 9600: ) (Hypervisor)\n"
      }
    ],
    "query": "SELECT\n      SERVERPROPERTY(\u0027Collation\u0027) AS [Collation],\n      SERVERPROPERTY(\u0027IsFullTextInstalled\u0027) AS [SqlFTinstalled],\n      SERVERPROPERTY(\u0027IsIntegratedSecurityOnly\u0027) AS [SqlIntSec],\n      SERVERPROPERTY(\u0027IsSingleUser\u0027) AS [IsSingleUser],\n      SERVERPROPERTY (\u0027FileStreamEffectiveLevel\u0027) AS [SqlFilestreamMode],\n      SERVERPROPERTY(\u0027IsPolybaseInstalled\u0027) AS [SqlPbInstalled],\n      SERVERPROPERTY(\u0027PolybaseRole\u0027) AS [SqlPbNodeRole],\n      SERVERPROPERTY(\u0027ProductMajorVersion\u0027) AS [SqlVersionMajor],\n      SERVERPROPERTY(\u0027ProductMinorVersion\u0027) AS [SqlVersionMinor],\n      SERVERPROPERTY(\u0027ProductBuild\u0027) AS [SqlVersionBuild],\n      SERVERPROPERTY(\u0027ProductBuildType\u0027) AS ProductBuildType,\n      SERVERPROPERTY(\u0027ProductLevel\u0027) AS ProductLevel,\n      SERVERPROPERTY(\u0027ProductUpdateLevel\u0027) AS ProductUpdateLevel,\n      SERVERPROPERTY(\u0027ProductUpdateReference\u0027) AS ProductUpdateReference,\n      RIGHT(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)),CHARINDEX(\u0027.\u0027, REVERSE(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)))) - 1) AS ProductRevision,\n      SERVERPROPERTY(\u0027EditionID\u0027) AS SQLEditionId,\n      SERVERPROPERTY(\u0027IsClustered\u0027) AS IsClustered,\n      SERVERPROPERTY(\u0027IsHadrEnabled\u0027) AS IsHadrEnabled,\n      SERVERPROPERTY(\u0027IsAdvancedAnalyticsInstalled\u0027) AS [SqlAdvAInstalled],\n      @@PACK_RECEIVED AS PacketReceived,\n      @@VERSION AS Version",
    "queryTimeInTicks": 0
  } ,
  {
    "hostName": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "domainHash": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "sqmId": "02AF58F5-753A-429C-96CD-3900E90DB990",
    "instanceName": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "schemaVersion": "3",
    "emitTime": "2016-09-08T17:20:24.9819144Z",
    "sessionId": "89decf9a-ad11-485c-94a7-fefb3a02ed86",
    "correlationId": 0,
    "sequence": 61,
    "clientVersion": "13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223)",
    "operatingSystem": "Microsoft Windows Server 2012 R2 Datacenter",
    "querySetVersion": "1.0.0.0",
    "traceName": "SQLServerPeriodicQueries",
    "queryIdentifier": "ExternalScriptStats.001",
    "data": [
      {
        "counter_name": "Total Executions                                                                                                                ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Parallel Executions                                                                                                             ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Streaming Executions                                                                                                            ",
        "cntr_value": "0"
      },
      {
        "counter_name": "SQL CC Executions                                                                                                               ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Implied Auth. Logins                                                                                                            ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Total Execution Time (ms)                                                                                                       ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Execution Errors                                                                                                                ",
        "cntr_value": "0"
      }
    ],  
    "query": "select counter_name, cntr_value from sys.dm_os_performance_counters where object_name like \u0027%External Scripts%\u0027",
    "queryTimeInTicks": 155834
  } 
```
## <a name="frequently-asked-questions"></a>Domande frequenti

**Come fanno gli amministratori di database a leggere i file di log del controllo locale?**
Questi file di log vengono scritti in formato JSON. Ogni riga corrisponde a un oggetto JSON che rappresenta un elemento di telemetria inviato a Microsoft. I nomi dei campi devono essere facilmente comprensibili. 

**Cosa accade se l'amministratore di database disabilita la raccolta di dati relativi all'utilizzo?**
Non verrà scritto alcun file del controllo locale. 

**Cosa accade se la connettività Internet non è disponibile o il computer si trova all'interno del firewall?**
I dati relativi all'utilizzo di SQL Server 2016 non verranno inviati a Microsoft. Se configurato correttamente, il computer proverà comunque a scrivere i log del controllo locale.

**Come fanno gli amministratori di database a disabilitare il controllo locale?**
Per eseguire questa operazione, rimuovere la voce della chiave del Registro di sistema UserRequestedLocalAuditDirectory.

**Chi può leggere i file di log del controllo locale?**
Tutti gli utenti dell'organizzazione che dispongono dell'accesso alla directory del controllo locale.

**Come fanno gli amministratori di database a gestire i file di log scritti nella directory designata?**
Gli amministratori di database devono gestire autonomamente la pulizia dei file nella directory per evitare un utilizzo eccessivo dello spazio su disco.

**Quale client o strumento è possibile usare per leggere l'output JSON?**
L'output può essere letti con il Blocco note, Visual Studio o qualsiasi lettore JSON di propria scelta.
In alternativa, è possibile leggere il file JSON e analizzare i dati in un'istanza di SQL Server 2016, come illustrato di seguito. Per altre informazioni su come leggere il file JSON in SQL Server, visitare [Importing JSON files into SQL Server using OPENROWSET (BULK) and OPENJSON (Transact-SQL)](http://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/10/07/bulk-importing-json-files-into-sql-server/)(Importazione di file JSON in SQL Server mediante OPENROWSET (BULK) e OPENJSON (Transact-SQL)).

```Transact-SQL
DECLARE @JSONFile AS VARCHAR(MAX)

-- Read the JSON file into variable 
SELECT @JSONFile = BulkColumn 
FROM OPENROWSET (BULK 'C:\SQLCEIPAudit\MSSQLSERVER\2016-09-08.json', SINGLE_CLOB) MyFile 

-- Check if the JSON file has been read properly and if it's in a JSON format
SELECT 
    @JSONFile LocalAuditOutput, 
    ISJSON(@JSONFile) IsFileInJSONFormat

-- Get the query identifier, query and the data (output of the query)   
SELECT 
    sequence,
    queryIdentifier,
    query,
    data
FROM OPENJSON(@JSONFile) 
    WITH (sessionId VARCHAR(64)
         ,sequence INT
         ,queryIdentifier VARCHAR(128)
         ,query VARCHAR(MAX)
         ,data NVARCHAR(MAX) AS JSON)
-- Get specific details about the output of "DatabaseProperties.001" query  
SELECT 
    QueryIdentifier,
    DatabaseID,
    CompatibilityLevel,
    IsQueryStoreOn
FROM OPENJSON(@JSONFile) 
    WITH (sessionId VARCHAR(64)
         ,sequence INT
         ,queryIdentifier VARCHAR(128)
         ,query VARCHAR(MAX)
         ,data NVARCHAR(MAX) AS JSON) 
    CROSS APPLY OPENJSON(data) 
        WITH (   DatabaseID varchar(128) '$.database_id'
                ,CompatibilityLevel varchar(128) '$.compatibility_level'
                ,IsQueryStoreOn varchar(128) '$.QS'
             )
WHERE queryIdentifier = 'DatabaseProperties.001'
```

## <a name="see-also"></a>Vedere anche
[Controllo locale per la raccolta di dati relativi all'utilizzo di SSMS](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-telemetry-ssms)

