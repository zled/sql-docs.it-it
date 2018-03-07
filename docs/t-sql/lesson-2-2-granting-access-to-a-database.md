---
title: Concessione dell'accesso a un Database | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 50badd521bde0d30021f7097040beb8492cb1d2e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-2-2---granting-access-to-a-database"></a>Lezione 2-2-la concessione dell'accesso a un Database
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]Mary dispone ora dell'accesso a questa istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ma non dispone dell'autorizzazione per accedere ai database. L'utente non dispone inoltre dell'accesso al proprio database predefinito **TestData** a meno che non lo si autorizzi in qualità di utente del database.  
  
Per concedere l'accesso all'utente Mary, passare al database **TestData** e quindi utilizzare l'istruzione CREATE USER per eseguire il mapping dell'account utente a un utente denominato Mary.  
  
### <a name="to-create-a-user-in-a-database"></a>Per creare un utente in un database  
  
1.  Digitare ed eseguire le istruzioni seguenti sostituendo `computer_name` con il nome del computer in uso per concedere all'utente `Mary` l'accesso al database `TestData` .  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
    L'utente Mary dispone ora dell'accesso a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e al database `TestData` .  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Creazione di viste e stored procedure](../t-sql/lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
  
