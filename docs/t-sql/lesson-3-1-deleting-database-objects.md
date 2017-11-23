---
title: Eliminazione di oggetti di Database | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d8e3d5eba52076ae58337fb9579781cad10a5f42
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-3-1---deleting-database-objects"></a>Lezione 3-1-eliminazione degli oggetti di Database
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]Per rimuovere tutte le tracce di questa esercitazione, è possibile eliminare solo il database. In questo argomento verranno comunque illustrate le procedure per annullare ogni azione eseguita nell'ambito dell'esercitazione.  
  
### <a name="removing-permissions-and-objects"></a>Rimozione di autorizzazioni e oggetti  
  
1.  Prima di eliminare gli oggetti, verificare di trovarsi nel database corretto:  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  Utilizzare l'istruzione `REVOKE` per rimuovere l'autorizzazione di esecuzione per `Mary` sulla stored procedure:  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  Utilizzare l'istruzione `DROP` per rimuovere l'autorizzazione di accesso per `Mary` al database `TestData` :  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  Utilizzare l'istruzione `DROP` per rimuovere l'autorizzazione di accesso per `Mary` all'istanza di [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]:  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  Utilizzare l'istruzione `DROP` per rimuovere la stored procedure `pr_Names`:  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  Utilizzare l'istruzione `DROP` per rimuovere la vista `vw_Names`:  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  Utilizzare l'istruzione `DELETE` per rimuovere tutte le righe della tabella `Products` :  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  Utilizzare l'istruzione `DROP` per rimuovere la tabella `Products` :  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. Non è possibile rimuovere il database `TestData` se è in uso. Passare pertanto a un altro database e quindi utilizzare l'istruzione `DROP` per rimuovere il database `TestData` :  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
In questo modo si conclude l'esercitazione per la scrittura di istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] . Tenere presente che questa esercitazione rappresenta una breve panoramica in cui non vengono descritte tutte le opzioni delle istruzioni utilizzate. La progettazione e la creazione di una struttura di database efficiente e la configurazione dell'accesso sicuro ai dati richiede un database più complesso di quello illustrato in questa esercitazione.  
  
## <a name="return-to-sql-server-tools-portal"></a>Torna al portale degli strumenti di SQL Server  
[Esercitazione: Scrittura di istruzioni Transact-SQL](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a>Vedere anche  
[REVOKE &#40;Transact-SQL&#41;](../t-sql/statements/revoke-transact-sql.md)  
[DROP USER &#40;Transact-SQL&#41;](../t-sql/statements/drop-user-transact-sql.md)  
[DROP LOGIN &#40;Transact-SQL&#41;](../t-sql/statements/drop-login-transact-sql.md)  
[DROP PROCEDURE &#40;Transact-SQL&#41;](../t-sql/statements/drop-procedure-transact-sql.md)  
[DROP VIEW &#40;Transact-SQL&#41;](../t-sql/statements/drop-view-transact-sql.md)  
[DELETE &#40;Transact-SQL&#41;](../t-sql/statements/delete-transact-sql.md)  
[DROP TABLE &#40;Transact-SQL&#41;](../t-sql/statements/drop-table-transact-sql.md)  
[DROP DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/drop-database-transact-sql.md)  
  
  
  
