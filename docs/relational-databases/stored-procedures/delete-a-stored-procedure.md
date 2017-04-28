---
title: Eliminare una stored procedure | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stored-Procs
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing stored procedures
- stored procedures [SQL Server], deleting
- deleting stored procedures
ms.assetid: 232dbf4d-392a-406f-af3a-579518cd8e46
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d9f9d65d2521299d34188897fbbf5675b5c9eea4
ms.lasthandoff: 04/11/2017

---
# <a name="delete-a-stored-procedure"></a>Eliminare una stored procedure
    
##  <a name="Top"></a> In questo argomento viene descritto come eliminare una stored procedure in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   **Before you begin:**  [Limitations and Restrictions](#Restrictions), [Security](#Security)  
  
-   **To delete a procedure, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 L'eliminazione di una stored procedure può causare errori negli oggetti e script dipendenti quando questi non vengono aggiornati per riflettere la rimozione della stored procedure. Tuttavia, se si crea una nuova stored procedure con lo stesso nome e gli stessi parametri per sostituire quella eliminata, gli altri oggetti che fanno riferimento ancora alla stored procedure verranno elaborati correttamente. Per altre informazioni, vedere [Visualizzare le dipendenze di una stored procedure](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per lo schema a cui appartiene la stored procedure oppure l'autorizzazione CONTROL per la stored procedure.  
  
##  <a name="Procedures"></a> Modalità di eliminazione di una stored procedure  
 È possibile usare uno dei seguenti elementi:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per eliminare una stored procedure in Esplora oggetti**  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere **Database**, espandere il database a cui appartiene la stored procedure, quindi espandere **Programmabilità**.  
  
3.  Espandere **Stored procedure**, fare clic con il pulsante destro del mouse sulla stored procedure da rimuovere e scegliere **Elimina**.  
  
4.  Per visualizzare gli oggetti dipendenti dalla stored procedure, fare clic su **Mostra dipendenze**.  
  
5.  Confermare che è stata selezionata la stored procedure corretta, quindi scegliere **OK**.  
  
6.  Rimuovere i riferimenti alla stored procedure da tutti gli oggetti e script dipendenti.  
  
###  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 **Per eliminare una stored procedure nell'editor di query**  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere **Database**ed espandere il database a cui appartiene la stored procedure. In alternativa, dalla barra degli strumenti selezionare il database dall'elenco di database disponibili.  
  
3.  Scegliere **Nuova query**dal menu File.  
  
4.  Ottenere il nome della stored procedure da rimuovere nel database corrente. Da Esplora oggetti espandere **Programmabilità** , quindi espandere **Stored procedure**. In alternativa, nell'editor di query eseguire l'istruzione riportata di seguito.  
  
    ```tsql  
    SELECT name AS procedure_name   
        ,SCHEMA_NAME(schema_id) AS schema_name  
        ,type_desc  
        ,create_date  
        ,modify_date  
    FROM sys.procedures;  
    ```  
  
5.  Copiare e incollare l'esempio seguente nell'editor di query e inserire il nome di una stored procedure da eliminare dal database corrente.  
  
    ```tsql  
    DROP PROCEDURE <stored procedure name>;  
    GO  
    ```  
  
6.  Rimuovere i riferimenti alla stored procedure da tutti gli oggetti e script dipendenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di una stored procedure](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [Modificare una stored procedure](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [Rinominare una stored procedure](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [Visualizzare la definizione di una stored procedure](../../relational-databases/stored-procedures/view-the-definition-of-a-stored-procedure.md)   
 [Visualizzare le dipendenze di una stored procedure](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)   
 [DROP PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-procedure-transact-sql.md)  
  
  
