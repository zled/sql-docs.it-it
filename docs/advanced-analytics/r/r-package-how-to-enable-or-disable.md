---
title: Abilitare o disabilitare la gestione dei pacchetti R per SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 01/04/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 35bcae1e29e9b640d2e04b9adc788e382b18b6e8
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="enable-or-disable-r-package-management-for-sql-server"></a>Abilitare o disabilitare la gestione dei pacchetti R per SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo descrive una nuova funzionalità di gestione pacchetti di SQL Server 2017, progettato per consentire all'amministratore di database controllare l'installazione del pacchetto nell'istanza utilizzando T-SQL anziché di R.

N seguito che frature di gestione il pacchetto è abilitato, è possibile utilizzare i comandi di R per installare i pacchetti in un frm database un client remoto.

> [!NOTE]
> Per impostazione predefinita, la funzionalità di gestione di pacchetto esterno per SQL Server è disabilitata, anche se le funzionalità di machine learning sono state installate. 

## <a name="enable-package-management"></a>Abilitare la gestione dei pacchetti

Per [abilitare](#bkmk_enable) questa funzionalità è un processo in due fasi, che richiede un amministratore del database:

1.  Abilitare la gestione dei pacchetti nell'istanza di SQL Server (una volta per ogni istanza di SQL Server)

2.  Abilitare la gestione dei pacchetti nel database di SQL (una volta per ogni database di SQL Server)

Per [disabilitare](#bkmk_disable) la funzionalità di gestione di pacchetti, invertire il processo per rimuovere i pacchetti a livello di database e le autorizzazioni e quindi rimuovere i ruoli del server:

1.  Disabilitare la gestione dei pacchetti in ogni database (una volta per ogni database)

2.  Disabilitare la gestione dei pacchetti nell'istanza di SQL Server (una volta per ogni istanza)

## <a name="bkmk_enable"></a>Abilitare la gestione dei pacchetti

Per abilitare o disabilitare la gestione dei pacchetti, utilizzare l'utilità della riga di comando **RegisterRExt.exe**, inclusa la **RevoScaleR** pacchetto.

1. Aprire un prompt dei comandi con privilegi elevati e passare alla cartella contenente l'utilità, RegisterRExt.exe. Il percorso predefinito è `<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe`.

2. Eseguire il comando seguente, che fornisce gli argomenti appropriati per l'ambiente:

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Questo comando crea gli oggetti a livello di istanza nel computer SQL Server che sono necessari per la gestione dei pacchetti. Il riavvio anche la finestra di avvio per l'istanza.

    Se non si specifica un'istanza, viene utilizzata l'istanza predefinita. Se non si specifica un utente, viene utilizzato il contesto di sicurezza corrente. Ad esempio, il comando seguente consente di gestione dei pacchetti nell'istanza nel percorso di RegisterRExt.exe, utilizzando le credenziali dell'utente che ha aperto il prompt dei comandi:

    `REgisterRExt.exe /installpkgmgmt`

2.  Per aggiungere Gestione dei pacchetti a un database specifico, eseguire il comando seguente da un prompt dei comandi con privilegi elevati:

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`
   
    Questo comando crea alcuni elementi del database, inclusi i seguenti ruoli del database che vengono utilizzati per controllare le autorizzazioni utente: `rpkgs-users`, `rpkgs-private`, e `rpkgs-shared`.

    Ad esempio, il comando seguente consente di gestione dei pacchetti nel database nell'istanza in cui viene eseguito RegisterRExt. Se non si specifica un utente, viene utilizzato il contesto di sicurezza corrente. 

    `RegisterRExt.exe /installpkgmgmt /database:TestDB`

3. Ripetere il comando per ogni database in cui installare i pacchetti.

4.  Per verificare che i nuovi ruoli sono stati creati correttamente, in SQL Server Management Studio, fare clic sul database, espandere **sicurezza**, espandere **ruoli predefiniti del Database**.

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

4.  Dopo aver abilitata la funzionalità, è possibile connettersi al server e installare o sincronizzare i pacchetti in modalità remota, utilizzando i comandi di R. Per un esempio del funzionamento, vedere [installare pacchetti aggiuntivi su SQL Server](install-additional-r-packages-on-sql-server.md).

## <a name="bkmk_disable"></a>Disabilitare la gestione dei pacchetti

1.  Da un prompt dei comandi con privilegi elevati, eseguire di nuovo l'utilità RegisterRExt e disabilitare la gestione dei pacchetti a livello di database:

    `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]`

    Questo comando rimuove gli oggetti di database correlati a gestione dei pacchetti dal database specificato. Inoltre, rimuove tutti i pacchetti che sono stati installati dal percorso di sistema del file protetto nel computer SQL Server.

2. Eseguire questo comando una volta per ogni database in cui è stato utilizzato Gestione dei pacchetti. 

3.  (Facoltativo) Dopo che tutti i database sono stati cancellati dei pacchetti utilizzando il passaggio precedente, eseguire il comando seguente da un prompt dei comandi con privilegi elevati:

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Questo comando rimuove la funzionalità di gestione del pacchetto dall'istanza. Potrebbe essere necessario riavviare manualmente il servizio Launchpad ancora una volta per visualizzare le modifiche.

## <a name="see-also"></a>Vedere anche

[Gestione dei pacchetti R per SQL Server](r-package-management-for-sql-server-r-services.md)
