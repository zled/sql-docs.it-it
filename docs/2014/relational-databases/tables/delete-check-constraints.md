---
title: Eliminare vincoli CHECK | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing constraints
- CHECK constraints, deleting
- constraints [SQL Server], deleting
- constraints [SQL Server], check
- deleting constraints
ms.assetid: 5f86c1a6-f5fa-4e77-a892-f6ae96fc0ab3
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d4a9a87f253f14df01165cf1099090e946dbff52
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246323"
---
# <a name="delete-check-constraints"></a>Eliminazione dei vincoli CHECK
  È possibile eliminare un vincolo CHECK in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'eliminazione dei vincoli CHECK consente di rimuovere le limitazioni sui valori dei dati accettati nella colonna o nella combinazione di colonne inclusa nell'espressione del vincolo.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per eliminare un vincolo CHECK:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-delete-a-check-constraint"></a>Per eliminare un vincolo CHECK  
  
1.  In **Esplora oggetti**, espandere la tabella con il vincolo CHECK.  
  
2.  Espandere  **Vincoli**.  
  
3.  Fare clic con il pulsante destro del mouse sul vincolo e scegliere **Elimina**.  
  
4.  Nella finestra di dialogo **Elimina oggetto** fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-delete-a-check-constraint"></a>Per eliminare un vincolo CHECK  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    ALTER TABLE dbo.DocExc   
    DROP CONSTRAINT CHK_ColumnD_DocExc;  
    GO  
    ```  
  
 Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).  
  
  
