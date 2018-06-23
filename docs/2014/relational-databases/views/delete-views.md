---
title: Eliminare viste | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-views
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dropping views
- deleting views
- views [SQL Server], deleting
- removing views
ms.assetid: 6823c7f8-06ca-4bda-8482-7092f03d52a0
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: a8ed1ad09f530575e94a61934f464ca3c2f2e6fa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157674"
---
# <a name="delete-views"></a>Eliminare viste
  È possibile eliminare (rimuovere) le viste in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  

  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Quando si rimuove una vista, dal catalogo di sistema vengono eliminate la definizione e altre informazioni della vista. Vengono inoltre eliminate tutte le autorizzazioni per la vista.  
  
-   Qualsiasi vista di una tabella che viene eliminata tramite `DROP TABLE` deve essere eliminata in modo esplicito utilizzando `DROP VIEW`.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È richiesta l'autorizzazione ALTER per l'autorizzazione SCHEMA o CONTROL per OBJECT.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-delete-a-view-from-a-database"></a>Per eliminare una vista da un database  
  
1.  In **Esplora oggetti**espandere il database contenente la vista da eliminare, quindi espandere la cartella **Viste** .  
  
2.  Fare clic con il pulsante destro del mouse sulla vista da eliminare e scegliere **Elimina**.  
  
3.  Nella finestra di dialogo **Elimina oggetto** fare clic su **OK**.  
  
    > [!IMPORTANT]  
    >  Fare clic su **Mostra dipendenze** nella finestra di dialogo **Elimina oggetto** per aprire la finestra di dialogo *Dipendenze di***nome_vista**. Verranno visualizzati tutti gli oggetti che dipendono dalla vista e tutti gli oggetti da cui dipende la vista.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-delete-a-view-from-a-database"></a>Per eliminare una vista da un database  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Nell'esempio si elimina la vista specificata solo se la vista già esiste.  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    IF OBJECT_ID ('HumanResources.EmployeeHireDate', 'V') IS NOT NULL  
    DROP VIEW HumanResources.EmployeeHireDate;  
    GO  
    ```  
  
 Per altre informazioni, vedere [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql).  
  
  
