---
title: Visualizzare la definizione di una tabella | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- showing table properties
- displaying table properties
- tables [SQL Server], properties
- viewing table properties
ms.assetid: 1865fb7c-f480-4100-9007-df5364cd002a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ff052e606045f004064c86c5cbec2248a2998c2e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222181"
---
# <a name="view-the-table-definition"></a>Visualizzare la definizione di una tabella
  È possibile visualizzare proprietà per una tabella in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per visualizzare le proprietà di tabella:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È possibile vedere solo proprietà in una tabella se si possiede la tabella o sono state concesse autorizzazioni a quella tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-show-table-properties-in-the-properties-window"></a>Per visualizzare le proprietà di una tabella nella finestra Proprietà  
  
1.  In Esplora oggetti selezionare la tabella per la quale si desidera mostrare le proprietà.  
  
2.  Fare clic con il pulsante destro del mouse sulla tabella, quindi scegliere **Proprietà** dal menu di scelta rapida. Per altre informazioni, vedere [Table Properties](table-properties-ssms.md).  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-show-table-properties"></a>Per mostrare le proprietà di tabella  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. Nell'esempio seguente vengono restituite tutte le colonne dalla vista del catalogo `sys.tables` per l'oggetto specificato.  
  
    ```  
    SELECT * FROM sys.tables  
    WHERE object_id = 1973582069;  
  
    ```  
  
 Per altre informazioni, vedere [sys.tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql).  
  
###  <a name="TsqlExample"></a>  
