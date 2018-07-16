---
title: Elencare le informazioni sulle categorie di processi | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 33cf862e752618b35c56d2e5c58f534ca03a347d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280817"
---
# <a name="list-job-category-information"></a>Elencare le informazioni sulle categorie di processi
  Come elencare le informazioni sulle categorie di processi nella [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[tsql](../../includes/tsql-md.md)] o SQL Server Management Objects.  

  
##  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  

  
##  <a name="TSQL"></a> Uso di Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>Per elencare le informazioni sulle categorie di processi  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_help_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).  
  
  
##  <a name="SMO"></a> Utilizzo di SQL Server Management Objects  
 **Per elencare le informazioni sulle categorie di processi**  
  
 Usare il `JobCategory` classe utilizzando un linguaggio di programmazione desiderato, ad esempio Visual Basic, Visual c# o PowerShell... Per altre informazioni, vedere [SQL Server Management Objects &#40;SMO&#41; Guida per programmatori](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).  
  
  
  
