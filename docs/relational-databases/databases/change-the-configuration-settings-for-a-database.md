---
title: "Modificare le impostazioni di configurazione per un database | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configurazione di database [SQL Server]"
  - "opzioni di configurazione [SQL Server], database"
  - "modifica delle impostazioni di configurazione di database"
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Modificare le impostazioni di configurazione per un database
  In questo argomento si illustra come modificare le opzioni a livello di database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Queste opzioni sono specifiche di ogni database e non hanno effetto su altri database.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per modificare le opzioni di configurazione per un database usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Queste opzioni possono essere modificate solo dall'amministratore di sistema, dal proprietario del database, dai membri dei ruoli predefiniti del server **sysadmin** e **dbcreator** e dai membri del ruolo predefinito del database **db_owner**.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per modificare le opzioni di configurazione per un database  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)], espandere il server, espandere **Database**, fare clic con il pulsante destro del mouse su un database e quindi scegliere **Proprietà**.  
  
2.  Nella finestra di dialogo **Proprietà database** fare clic su **Opzioni** per accedere alla maggior parte delle impostazioni di configurazione. Le configurazioni di file, filegroup, mirroring e log shipping sono disponibili nelle rispettive pagine.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per modificare le opzioni di configurazione per un database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio si impostano le opzioni relative al modello di recupero e alla verifica delle pagine di dati per il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../relational-databases/databases/codesnippet/tsql/change-the-configuration_1.sql)]  
  
 Per altri esempi, vedere [Opzioni di ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
## Vedere anche  
 [Livello di compatibilità ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md)   
 [Mirroring del database di ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md)   
 [Rinominare un database](../../relational-databases/databases/rename-a-database.md)   
 [Compattare un database](../../relational-databases/databases/shrink-a-database.md)  
  
  