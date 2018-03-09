---
title: Disabilitare i vincoli CHECK con le istruzioni INSERT e UPDATE | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CHECK constraints, disabling
- constraints [SQL Server], disabling
- disabling constraints
- constraints [SQL Server], check
ms.assetid: c7287ad1-50d2-4e80-bc0c-b5570f7e5f69
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 8cdb86213d6c30c14aa886690c64c7998e6fba9a
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="disable-check-constraints-with-insert-and-update-statements"></a>Disabilitazione di vincoli CHECK con le istruzioni INSERT e UPDATE
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  È possibile disabilitare un vincolo CHECK per transazioni INSERT e UPDATE in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Dopo aver disabilitato i vincoli CHECK, gli inserimenti o gli aggiornamenti successivi della colonna non saranno convalidati in base alle condizioni del vincolo. Usare questa opzione se si è sicuri che i nuovi dati violeranno il vincolo esistente o se il vincolo si applica solo ai dati già presenti nel database.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per disabilitare un vincolo CHECK per le istruzioni INSERT e UPDATE:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a>Per disabilitare un vincolo CHECK per le istruzioni INSERT e UPDATE  
  
1.  In **Esplora oggetti**, espandere la tabella contenente il vincolo che si desidera modificare, quindi espandere la cartella **Vincoli** .  
  
2.  Fare clic con il pulsante destro del mouse sul vincolo e scegliere **Modifica**.  
  
3.  Nella griglia, in **Progettazione tabelle**, fare clic su **Attiva per istruzioni INSERTs e UPDATEs** , quindi scegliere **No** dal menu a discesa.  
  
4.  Scegliere **Chiudi**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-disable-a-check-constraint-for-insert-and-update-statements"></a>Per disabilitare un vincolo CHECK per le istruzioni INSERT e UPDATE  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare gli esempi seguenti nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT CK_PurchaseOrderHeader_Freight;   
    GO  
    ```  
  
 Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  
