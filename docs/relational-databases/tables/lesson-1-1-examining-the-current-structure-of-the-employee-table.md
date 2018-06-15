---
title: Esame della struttura corrente della tabella Employee | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- examining the current structure of the employee
ms.assetid: d546a820-105a-417d-ac35-44a6d1d70ac6
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 620defd42e27b122a92ee145da6b4b14d1cbf996
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "33006638"
---
# <a name="lesson-1-1---examining-the-current-structure-of-the-employee-table"></a>Lezione 1-1: Esame della struttura corrente della tabella Employee
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] (o versione successiva) contiene una tabella **Employee** nello schema **HumanResources**. Per evitare di modificare la tabella originale, in questo passaggio viene creata una copia della tabella **Employee** denominata **EmployeeDemo**. Per semplificare l'esempio, copiare solo cinque colonne della tabella originale. Eseguire quindi una query sulla tabella **HumanResources.EmployeeDemo** per esaminare il modo in cui viene strutturata una tabella senza usare il tipo di dati **hierarchyid** .  
  
### <a name="to-copy-the-employee-table"></a>Per copiare la tabella Employee  
  
1.  In una finestra editor di query, eseguire il codice seguente per copiare la struttura della tabella e i dati della tabella **Employee** in una tabella nuova denominata **EmployeeDemo**. Poiché la tabella originale usa già hierarchyid, questa query essenzialmente rende flat la gerarchia per recuperare il manager del dipendente. Nelle parti successive di questa lezione questa gerarchia verrà ricostruita.
  
    ```  
    USE AdventureWorks ;  
    GO  
  
    SELECT emp.BusinessEntityID AS EmployeeID, emp.LoginID, 
      (SELECT  man.BusinessEntityID FROM HumanResources.Employee man 
            WHERE emp.OrganizationNode.GetAncestor(1)=man.OrganizationNode OR 
                (emp.OrganizationNode.GetAncestor(1) = 0x AND man.OrganizationNode IS NULL)) AS ManagerID
        , emp.JobTitle, emp.HireDate
    INTO HumanResources.EmployeeDemo   
    FROM HumanResources.Employee emp ;
    GO
    ```  
  
### <a name="to-examine-the-structure-and-data-of-the-employeedemo-table"></a>Per esaminare la struttura e i dati della tabella EmployeeDemo  
  
-   Questa nuova tabella **EmployeeDemo** rappresenta una tabella tipica di un database esistente di cui si può eseguire la migrazione a una struttura nuova. In una finestra editor di query, eseguire il codice seguente per visualizzare il modo in cui la tabella utilizza un self-join per visualizzare le relazioni dipendente/responsabile:  
  
    ```  
    SELECT   
        Mgr.EmployeeID AS MgrID, Mgr.LoginID AS Manager,   
        Emp.EmployeeID AS E_ID, Emp.LoginID, Emp.JobTitle  
    FROM HumanResources.EmployeeDemo AS Emp  
    LEFT JOIN HumanResources.EmployeeDemo AS Mgr  
    ON Emp.ManagerID = Mgr.EmployeeID  
    ORDER BY MgrID, E_ID  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    ```  
    MgrID Manager                 E_ID LoginID                  JobTitle  
    NULL    NULL    1   adventure-works\ken0    Chief Executive Officer
    1   adventure-works\ken0    2   adventure-works\terri0  Vice President of Engineering
    1   adventure-works\ken0    16  adventure-works\david0  Marketing Manager
    1   adventure-works\ken0    25  adventure-works\james1  Vice President of Production
    1   adventure-works\ken0    234 adventure-works\laura1  Chief Financial Officer
    1   adventure-works\ken0    263 adventure-works\jean0   Information Services Manager
    1   adventure-works\ken0    273 adventure-works\brian3  Vice President of Sales
    2   adventure-works\terri0  3   adventure-works\roberto0    Engineering Manager
    3   adventure-works\roberto0    4   adventure-works\rob0    Senior Tool Designer
    ...  
    ```  
  
    Viene generato un totale di 290 righe di risultati.  
  
Con la clausola **ORDER BY** , i report diretti di ogni livello di gestione vengono elencati insieme nell'output. Ad esempio, tutti i sette dipendenti diretti di **MgrID** 1 (ken0) vengono elencati uno accanto all'altro. Anche se non impossibile, è molto più difficile raggruppare tutti coloro che in ultima istanza sono dipendenti di **MgrID** 1.  
  
Nell'attività successiva verrà creata una nuova tabella con un tipo di dati **hierarchyid** e verranno spostati i dati nella nuova tabella.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Popolamento di una tabella con dati gerarchici esistenti](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md)  
  
  
  
