---
title: Concessione dell'accesso a un Database | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 30de5de3d238905802e80d433c2df7deaf058929
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-2---granting-access-to-a-database"></a>Lezione 2-2-la concessione dell'accesso a un Database
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
  
  
  

