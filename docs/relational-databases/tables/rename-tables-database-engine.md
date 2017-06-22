---
title: Rinominare tabelle (motore di database) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- table renaming [SQL Server]
- table names [SQL Server]
- tables [SQL Server], Visual Database Tools
- renaming tables
ms.assetid: 2f5c922d-4d71-4694-9fca-28dd99375799
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d65c475509d57577f691e656157c7754c7d8549f
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="rename-tables-database-engine"></a>Ridenominazione di tabelle (motore di database)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  È possibile rinominare una tabella in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!CAUTION]  
>  Fare attenzione prima di rinominare una tabella. Se query, viste, funzioni definite dall'utente, stored procedure o programmi esistenti fanno riferimento a tale tabella, la modifica del nome renderà questi oggetti non validi.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per rinominare una tabella:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Se una tabella viene ridenominata, i riferimenti a tale tabella non vengono ridenominati automaticamente ed è necessario modificare manualmente tutti gli oggetti che fanno riferimento alla tabella rinominata. Se, ad esempio, si rinomina una tabella a cui viene fatto riferimento all'interno di un trigger, è necessario modificare il trigger in base al nuovo nome della tabella. Utilizzare [sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) per elencare le dipendenze della tabella prima di rinominarla.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-rename-a-table"></a>Per rinominare una tabella  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse sulla tabella da rinominare, quindi selezionare **Progetta** dal menu di scelta rapida.  
  
2.  Scegliere **Proprietà** dal menu **Visualizza**.  
  
3.  Nella finestra **Proprietà** digitare un nuovo nome per la tabella nel campo relativo al valore **Nome** .  
  
4.  Per annullare questa azione, premere ESC prima di uscire dal campo.  
  
5.  Dal menu **File** scegliere **Salva***nome tabella*.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### <a name="to-rename-a-table"></a>Per rinominare una tabella  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Nell'esempio seguente la tabella `SalesTerritory` viene rinominata in `SalesTerr` nello schema `Sales` . Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE AdventureWorks2012;   
    GO  
    EXEC sp_rename 'Sales.SalesTerritory', 'SalesTerr';  
    ```  
  
 Per altri esempi, vedere [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md).  
  
  
