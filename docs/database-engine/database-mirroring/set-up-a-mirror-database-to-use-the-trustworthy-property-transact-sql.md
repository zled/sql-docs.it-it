---
title: "Impostazione di un database mirror per l&#39;utilizzo della propriet&#224; Trustworthy (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/09/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TRUSTWORTHY - opzione di database"
  - "database mirror [SQL Server]"
  - "mirroring del database [SQL Server], sicurezza"
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# Impostazione di un database mirror per l&#39;utilizzo della propriet&#224; Trustworthy (Transact-SQL)
  Quando viene eseguito il backup di un database, la proprietà TRUSTWORTHY del database viene impostata su OFF. Di conseguenza, la proprietà TRUSTWORTHY di un nuovo database mirror è sempre impostata su OFF. Se il database deve risultare attendibile dopo un failover, è necessario eseguire passaggi di configurazione aggiuntivi dopo l'avvio del mirroring.  
  
> [!NOTE]  
>  Per informazioni su questa proprietà di database, vedere [Proprietà di database TRUSTWORTHY](../../relational-databases/security/trustworthy-database-property.md).  
  
## Procedura  
  
#### Per impostare un database mirror per l'utilizzo della proprietà Trustworthy  
  
1.  Sull'istanza del server principale verificare che nel database principale la proprietà Trustworthy sia impostata su ON.  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     Per altre informazioni, vedere [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).  
  
2.  Dopo l'avvio del mirroring, verificare che il database sia impostato quale database principale, che nella sessione venga utilizzata una modalità operativa sincrona e che la sessione sia già sincronizzata.  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     Per altre informazioni, vedere [sys.database_mirroring &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md).  
  
3.  Dopo la sincronizzazione della sessione di mirroring, eseguire manualmente il failover sul database mirror.  
  
     Questa operazione può essere eseguita in SQL Server Management Studio o mediante Transact-SQL:  
  
    -   [Eseguire il failover manuale di una sessione di mirroring del database &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Eseguire il failover manuale di una sessione di mirroring del database &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  Impostare la proprietà Trustworthy del database su ON utilizzando il comando ALTER DATABASE seguente:  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     Per altre informazioni, vedere[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).  
  
5.  Facoltativamente, eseguire di nuovo il failover manuale per tornare al database principale originale.  
  
6.  Facoltativamente, passare in modalità asincrona a prestazioni elevate impostando SAFETY su OFF e verificando che anche WITNESS sia impostato su OFF.  
  
     In Transact-SQL:  
  
    -   [Modificare la sicurezza delle transazioni in una sessione di mirroring del database &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [Rimuovere il server di controllo del mirroring da una sessione di mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     In SQL Server Management Studio:  
  
    -   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish database mirroring session - windows authentication.md)  
  
## Vedere anche  
 [Proprietà di database TRUSTWORTHY](../../relational-databases/security/trustworthy-database-property.md)   
 [Impostazione di un database mirror crittografato](../../database-engine/database-mirroring/set-up-an-encrypted-mirror-database.md)  
  
  