---
title: "Eliminazione di relazioni di chiave esterna | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "chiavi esterne [SQL Server], eliminazione"
  - "rimozione di chiavi esterne"
  - "eliminazione di chiavi esterne"
ms.assetid: 9c9e9ae4-9e03-4137-acb6-b18928a0c4ca
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Eliminazione di relazioni di chiave esterna
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  È possibile eliminare un vincolo di chiave esterna in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'eliminazione di un vincolo di chiave esterna comporta la rimozione del requisito di attivazione dell'integrità referenziale.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per eliminare un vincolo di chiave esterna utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per eliminare un vincolo di chiave esterna  
  
1.  In **Esplora oggetti**espandere la tabella contenente il vincolo, quindi espandere **Chiavi**.  
  
2.  Fare clic con il pulsante destro del mouse sul vincolo e selezionare **Elimina**.  
  
3.  Nella finestra di dialogo **Elimina oggetto** fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per eliminare un vincolo di chiave esterna  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.DocExe   
    DROP CONSTRAINT FK_Column_B;   
    GO  
    ```  
  
 Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
  