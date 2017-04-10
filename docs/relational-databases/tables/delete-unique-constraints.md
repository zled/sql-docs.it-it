---
title: "Eliminazione di vincoli univoci | Microsoft Docs"
ms.custom: ""
ms.date: "10/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rimozione di vincoli"
  - "vincoli UNIQUE [SQL Server], eliminazione"
  - "vincoli [SQL Server], eliminazione"
  - "eliminazione di vincoli"
  - "vincoli [SQL Server], unique"
ms.assetid: 71e563fc-f5d7-4c2e-a42f-f0695a831f32
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Eliminazione di vincoli univoci
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  È possibile eliminare un vincolo univoco in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'eliminazione di un vincolo univoco consente di rimuovere il requisito di univocità per i valori immessi nella colonna o nella combinazione di colonne inclusa nell'espressione del vincolo ed elimina l'indice univoco corrispondente.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per eliminare un vincolo univoco:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per eliminare un vincolo univoco utilizzando Esplora oggetti  
  
1.  In Esplora oggetti, espandere la tabella contenente il vincolo univoco, quindi espandere la cartella **Vincoli**.  
  
2.  Fare clic con il pulsante destro del mouse sulla chiave e selezionare **Elimina**.  
  
3.  Nella finestra di dialogo **Elimina oggetto** verificare che venga specificata la chiave corretta e fare clic su **OK**.  
  
#### Per eliminare un vincolo univoco utilizzando Progettazione tabelle  
  
1.  In **Esplora oggetti** fare clic con il pulsante destro del mouse sulla tabella con il vincolo UNIQUE e selezionare **Progetta**.  
  
2.  Scegliere **Indici/chiavi** dal menu **Progettazione tabelle**.  
  
3.  Nella finestra di dialogo **Indici/chiavi** selezionare la chiave univoca dall'elenco **Chiave o indice primario/univoco selezionato**.  
  
4.  Fare clic su **Elimina**.  
  
5.  Nel menu **File** scegliere **Salva** *table name*.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per eliminare un vincolo univoco  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- Return the name of unique constraint.  
    SELECT name  
    FROM sys.objects  
    WHERE type = 'UQ' AND OBJECT_NAME(parent_object_id) = N' DocExc';  
    GO  
    -- Delete the unique constraint.  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT UNQ_ColumnB_DocExc;  
    GO  
    ```  
  
 Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md) e [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  