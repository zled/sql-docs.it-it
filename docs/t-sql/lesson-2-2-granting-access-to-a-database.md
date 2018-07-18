---
title: Concessione dell'accesso a un database | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 75d4f048573ce60b0be6704196b376c8136aa213
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424090"
---
# <a name="lesson-2-2---granting-access-to-a-database"></a>Lezione 2-2 - Concessione dell'accesso a un database
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
L'utente Mary dispone ora dell'accesso all'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ma non delle autorizzazioni necessarie per accedere ai database. L'utente non dispone inoltre dell'accesso al proprio database predefinito **TestData** a meno che non lo si autorizzi in qualità di utente del database.  
  
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
  
  
  
