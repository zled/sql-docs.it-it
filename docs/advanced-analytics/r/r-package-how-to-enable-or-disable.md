---
title: Abilitare o disabilitare la gestione remota di pacchetto R per SQL Server Machine Learning | Documenti Microsoft
description: Abilitare la gestione remota di pacchetto R in SQL Server 2016 R Services o SQL Server 2017 Machine Learning Services (In-Database)
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/10/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 88604b48f93a7ec322e5e7f9a9bdba6b9eb2cc3c
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/08/2018
---
# <a name="enable-or-disable-remote-package-management-for-sql-server"></a>Abilitare o disabilitare la gestione di pacchetti remoti per SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo viene descritto come abilitare la gestione dei pacchetti di R da un'istanza remota di Server di Machine Learning. Dopo aver abilitata la funzionalità di gestione di pacchetti, è possibile utilizzare i comandi RevoScaleR per installare i pacchetti in un database da un client remoto.

> [!NOTE]
> Gestione delle librerie R è attualmente supportata; supporto per Python è della mappa.

Per impostazione predefinita, la funzionalità di gestione di pacchetto esterno per SQL Server è disabilitata, anche se le funzionalità di machine learning sono state installate. È necessario eseguire uno script separato per abilitare la funzionalità, come descritto nella sezione successiva.

## <a name="overview-of-process-and-tools"></a>Panoramica del processo e strumenti

Per abilitare o disabilitare la gestione dei pacchetti, utilizzare l'utilità della riga di comando **RegisterRExt.exe**, inclusa la **RevoScaleR** pacchetto.

[Abilitazione](#bkmk_enable) questa funzionalità è un processo in due fasi, che richiede un amministratore del database: abilitare la gestione dei pacchetti nell'istanza di SQL Server (una volta per ogni istanza di SQL Server) e quindi abilitare la gestione dei pacchetti nel database SQL (una volta per SQL Server database).

[La disabilitazione di](#bkmk_disable) la funzionalità di gestione del pacchetto richiede anche passaggi multipel: rimuovere pacchetti a livello di database e le autorizzazioni (una volta per ogni database) e quindi rimuovere i ruoli del server (una volta per ogni istanza).

## <a name="bkmk_enable"></a> Abilitare la gestione dei pacchetti

1. Aprire un prompt dei comandi con privilegi elevati e passare alla cartella contenente l'utilità, RegisterRExt.exe. Il percorso predefinito è `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Eseguire il comando seguente, che fornisce gli argomenti appropriati per l'ambiente:

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Questo comando crea gli oggetti a livello di istanza nel computer SQL Server che sono necessari per la gestione dei pacchetti. Il riavvio anche la finestra di avvio per l'istanza.

    Se non si specifica un'istanza, viene utilizzata l'istanza predefinita. Se non si specifica un utente, viene utilizzato il contesto di sicurezza corrente. Ad esempio, il comando seguente consente di gestione dei pacchetti nell'istanza nel percorso di RegisterRExt.exe, utilizzando le credenziali dell'utente che ha aperto il prompt dei comandi:

    `REgisterRExt.exe /installpkgmgmt`

3. Per aggiungere Gestione dei pacchetti a un database specifico, eseguire il comando seguente da un prompt dei comandi con privilegi elevati:

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Questo comando crea alcuni elementi del database, inclusi i seguenti ruoli del database che vengono utilizzati per controllare le autorizzazioni utente: `rpkgs-users`, `rpkgs-private`, e `rpkgs-shared`.

    Ad esempio, il comando seguente consente di gestione dei pacchetti nel database nell'istanza in cui viene eseguito RegisterRExt. Se non si specifica un utente, viene utilizzato il contesto di sicurezza corrente.

    `RegisterRExt.exe /installpkgmgmt /database:TestDB`

4. Ripetere il comando per ogni database in cui installare i pacchetti.

5. Per verificare che i nuovi ruoli sono stati creati correttamente, in SQL Server Management Studio, fare clic sul database, espandere **sicurezza**, espandere **ruoli predefiniti del Database**.

    È anche possibile eseguire una query su Sys. database_principals, ad esempio le operazioni seguenti:

    ```SQL
    SELECT pr.principal_id, pr.name, pr.type_desc,   
        pr.authentication_type_desc, pe.state_desc,   
        pe.permission_name, s.name + '.' + o.name AS ObjectName  
    FROM sys.database_principals AS pr  
    JOIN sys.database_permissions AS pe  
        ON pe.grantee_principal_id = pr.principal_id  
    JOIN sys.objects AS o  
        ON pe.major_id = o.object_id  
    JOIN sys.schemas AS s  
        ON o.schema_id = s.schema_id;
    ```

Dopo avere abilitato questa funzionalità, è possibile utilizzare la funzione RevoScaleR per installare o disinstallare pacchetti da un client remoto di R.

## <a name="bkmk_disable"></a> Disabilitare la gestione dei pacchetti

1. Da un prompt dei comandi con privilegi elevati, eseguire di nuovo l'utilità RegisterRExt e disabilitare la gestione dei pacchetti a livello di database:

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Questo comando rimuove gli oggetti di database correlati a gestione dei pacchetti dal database specificato. Inoltre, rimuove tutti i pacchetti che sono stati installati dal percorso di sistema del file protetto nel computer SQL Server.

2. Ripetere questo comando in ciascun database in cui è stato utilizzato Gestione dei pacchetti.

3.  (Facoltativo) Dopo che tutti i database sono stati cancellati dei pacchetti utilizzando il passaggio precedente, eseguire il comando seguente da un prompt dei comandi con privilegi elevati:

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Questo comando rimuove la funzionalità di gestione del pacchetto dall'istanza. Potrebbe essere necessario riavviare manualmente il servizio Launchpad ancora una volta per visualizzare le modifiche.

