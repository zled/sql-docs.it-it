---
title: "Visualizzare o modificare le propriet&#224; di una condizione della gestione basata su criteri | Microsoft Docs"
ms.custom: ""
ms.date: "10/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Gestione basata su criteri, visualizzazione delle condizioni dei criteri"
  - "Gestione basata su criteri, modifica delle condizioni dei criteri"
ms.assetid: 890d7384-8444-4767-bb6f-f5debb155747
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Visualizzare o modificare le propriet&#224; di una condizione della gestione basata su criteri
  In questo argomento verrà descritto come visualizzare o modificare le proprietà di una condizione della gestione basata su criteri in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  

  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  

  
####  <a name="Permissions"></a> Permissions  
 È necessaria l'appartenenza al ruolo PolicyAdministratorRole nel database msdb.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per visualizzare o modificare le proprietà di una condizione  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server contenente la condizione da visualizzare o modificare.  
  
2.  Fare clic sul segno più per espandere la cartella **Gestione** .  
  
3.  Fare clic sul segno più per espandere la cartella **Gestione criteri**.  
  
4.  Fare clic sul segno più per espandere la cartella **Condizioni** .  
  
5.  Fare clic con il pulsante destro del mouse sulla condizione da visualizzare o modificare e scegliere **Proprietà**. Per altre informazioni sulle opzioni disponibili nella finestra di dialogo **Apri condizione –***nome_condizione*, vedere [Finestra di dialogo Crea nuova condizione o Apri condizione, pagina Generale](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-general-page.md), [Finestra di dialogo Apri condizione, pagina Criteri dipendenti](../../relational-databases/policy-based-management/open-condition-dialog-box-dependent-policies-page.md), [Finestra di dialogo Crea nuova condizione o Apri condizione, pagina Descrizione](../../relational-databases/policy-based-management/create-new-condition-or-open-condition-dialog-box-description-page.md) e [Finestra di dialogo Modifica avanzata &#40;Condizione&#41;](../../relational-databases/policy-based-management/advanced-edit-condition-dialog-box.md).  
  
6.  Al termine, fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per visualizzare le proprietà di una condizione  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE msdb;  
    GO  
    SELECT name,  
       description,  
       facet,  
       expression,  
       is_name_condition,  
       obj_name  
    FROM syspolicy_conditions;  
    GO  
  
    ```  
  
 Per altre informazioni, vedere [syspolicy_conditions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syspolicy-conditions-transact-sql.md).  
  
  