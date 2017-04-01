---
title: "Come abilitare o disabilitare la gestione dei pacchetti R | Microsoft Docs"
ms.custom: ""
ms.date: "12/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e384893-04da-43f9-b100-bfe99888f085
caps.latest.revision: 7
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
---
# Come abilitare o disabilitare la gestione dei pacchetti R

Per impostazione predefinita, la gestione dei pacchetti è disabilitata in un'istanza di SQL Server, anche se R Services è installato. Per abilitare questa funzionalità, è necessario eseguire un processo in due passaggi da un amministratore del database: 

1. Abilitare la gestione dei pacchetti nell'istanza di SQL Server (una volta per ogni istanza di SQL Server) 
2. Abilitare la gestione dei pacchetti nel database di SQL (una volta per ogni database di SQL Server) 


Quando si disabilita la funzionalità di gestione pacchetti, invertire la procedura per rimuovere le autorizzazioni e i pacchetti a livello di database e quindi rimuovere i ruoli del server:
 
1. Disabilitare la gestione dei pacchetti in ogni database (una volta per ogni database) 
2. Disabilitare la gestione dei pacchetti nell'istanza di SQL Server (una volta per ogni istanza) 

> [!IMPORTANT]
> Questa funzionalità è in fase di sviluppo. Tenere presente che la sintassi o la funzionalità può cambiare nelle versioni successive. 

### <a name="to-enable-package-management"></a>Per abilitare la gestione dei pacchetti

Per abilitare o disabilitare la gestione dei pacchetti, è necessaria l'utilità della riga di comando **RegisterRExt.exe**, inclusa nel pacchetto **RevoScaleR** installato con SQL Server R Services. Il percorso predefinito è:

`<SQLInstancePath>\R_SERVICES\library\RevoScaleR\rxLibs\x64\RegisterRExe.exe` 
    
1. Aprire un prompt dei comandi con privilegi elevati e usare il comando seguente:

    `RegisterRExt.exe /installpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Questo comando crea gli elementi a livello di istanza nel computer SQL Server necessari per la gestione dei pacchetti. 

2. Per aggiungere la gestione dei pacchetti a livello di database, per ogni database in cui devono essere installati i pacchetti, eseguire il comando seguente da un prompt dei comandi con privilegi elevati: 

    `RegisterRExt.exe /installpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]` 

    Questo comando crea alcuni elementi del database, inclusi i ruoli di database seguenti necessari per il controllo delle autorizzazioni utente: **rpkgs-users**, **rpkgs-private** e **rpkgs-shared** 

### <a name="to-disable-package-management"></a>Per disabilitare la gestione dei pacchetti 

1. Da un prompt dei comandi con privilegi elevati, eseguire il comando seguente per disabilitare la gestione dei pacchetti a livello di database:

   `RegisterRExt.exe /uninstallpkgmgmt /database:databasename [/instance:name] [/user:username] [/password:*|password]` 

    Questo comando rimuoverà gli elementi del database correlati alla gestione dei pacchetti dal database specificato.  Il comando rimuoverà anche tutti i pacchetti installati per ogni database dal percorso del file di sistema protetto nel computer SQL Server.
    
    Il comando deve essere eseguito una volta per ogni database in cui è stata usata la gestione dei pacchetti.
 
2. (Facoltativo) Per rimuovere completamente la funzionalità di gestione pacchetti dall'istanza, dopo che tutti i database sono stati cancellati dai pacchetti usando il passaggio precedente, eseguire il comando seguente da un prompt dei comandi con privilegi elevati:

    `RegisterRExt.exe /uninstallpkgmgmt [/instance:name] [/user:username] [/password:*|password]`

    Questo comando rimuove gli elementi a livello di istanza usati da gestione pacchetti dall'istanza di SQL Server. 


## <a name="see-also"></a>Vedere anche
[R Package Management for SQL Server R Services](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md) (Gestione dei pacchetti per SQL Server R Services)