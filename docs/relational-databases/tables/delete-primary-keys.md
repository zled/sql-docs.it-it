---
title: "Eliminazione di chiavi primarie | Microsoft Docs"
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
  - "rimozione di chiavi primarie"
  - "eliminazione di chiavi primarie"
  - "chiavi primarie [SQL Server], eliminazione"
ms.assetid: c472e465-7bdd-4d74-8fc9-e47fca007ccb
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Eliminazione di chiavi primarie
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  È possibile eliminare una chiave primaria in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Quando viene eliminata la chiave primaria, viene eliminato l'indice corrispondente.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per eliminare una chiave primaria:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per eliminare un vincolo chiave primaria utilizzando Esplora oggetti  
  
1.  In Esplora oggetti, espandere la tabella contenente la chiave primaria, quindi espandere la cartella **Chiavi**.  
  
2.  Fare clic con il pulsante destro del mouse sulla chiave e scegliere **Elimina**.  
  
3.  Nella finestra di dialogo **Elimina oggetto** verificare che venga specificata la chiave corretta e fare clic su **OK**.  
  
#### Per eliminare un vincolo chiave primaria utilizzando Progettazione tabelle  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse sulla tabella con la chiave primaria e scegliere **Progetta**.  
  
2.  Nella griglia della tabella fare clic con il pulsante destro del mouse sulla riga con la chiave primaria, quindi scegliere **Rimuovi chiave primaria** per attivare o disattivare l'impostazione.  
  
    > [!NOTE]  
    >  Per annullare questa operazione, chiudere la tabella senza salvare le modifiche. L'eliminazione di una chiave primaria non può essere annullata senza perdere tutte le altre modifiche apportate alla tabella.  
  
3.  Nel menu **File** scegliere **Salva***table name*.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per eliminare un vincolo di chiave primaria  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. Nell'esempio viene prima identificato il nome del vincolo di chiave primaria, quindi questo viene eliminato.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    -- Return the name of primary key.  
    SELECT name  
    FROM sys.key_constraints  
    WHERE type = 'PK' AND OBJECT_NAME(parent_object_id) = N'TransactionHistoryArchive';  
    GO  
    -- Delete the primary key constraint.  
    ALTER TABLE Production.TransactionHistoryArchive  
    DROP CONSTRAINT PK_TransactionHistoryArchive_TransactionID;   
    GO  
    ```  
  
 Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md) e [sys.key_constraints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)  
  
###  <a name="TsqlExample"></a>  