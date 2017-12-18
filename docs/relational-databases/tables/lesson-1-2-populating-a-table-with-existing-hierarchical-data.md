---
title: Popolamento di una tabella con dati gerarchici esistenti | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: HierarchyID
ms.assetid: fd943d84-dbe6-4a05-912b-c88164998d80
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 25feafb61615372739cc6997666cee5841424bb9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="lesson-1-2---populating-a-table-with-existing-hierarchical-data"></a>Lezione 1-2: Popolamento di una tabella con dati gerarchici esistenti
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] Questa attività consente di creare una nuova tabella e popolarla con i dati della tabella **EmployeeDemo**. Questa attività prevede i passaggi seguenti:  
  
-   Creare una tabella nuova contenente una colonna **hierarchyid** . Questa colonna può sostituire le colonne **EmployeeID** e **ManagerID** esistenti. Tuttavia, tali colonne verranno mantenute. Questo avviene perché le applicazioni esistenti potrebbero riferirsi a tali colonne e potrebbero aiutare a capire i dati dopo il trasferimento. La definizione della tabella specifica che **OrgNode** è la chiave primaria che richiede alla colonna di contenere i valori univoci. L'indice cluster della colonna **OrgNode** archivierà la data nella sequenza **OrgNode** .  
  
-   Creare una tabella temporanea utilizzata per rilevare il numero di dipendenti che riportano direttamente a ogni responsabile.  
  
-   Popolare la nuova tabella usando i dati dalla tabella **EmployeeDemo** .  
  
### <a name="to-create-a-new-table-named-neworg"></a>Per creare una nuova tabella denominata NewOrg  
  
-   In una finestra dell'editor di query eseguire il codice seguente per creare una nuova tabella denominata **HumanResources.NewOrg**:  
  
    ```  
    CREATE TABLE NewOrg  
    (  
      OrgNode hierarchyid,  
      EmployeeID int,  
      LoginID nvarchar(50),  
      ManagerID int  
    CONSTRAINT PK_NewOrg_OrgNode  
      PRIMARY KEY CLUSTERED (OrgNode)  
    );  
    GO  
    ```  
  
### <a name="to-create-a-temporary-table-named-children"></a>Per creare una tabella temporanea denominata #Children  
  
1.  Creare una tabella temporanea denominata **#Children** con una colonna denominata **Num** che conterrà il numero di elementi figlio per ogni nodo:  
  
    ```  
    CREATE TABLE #Children   
       (  
        EmployeeID int,  
        ManagerID int,  
        Num int  
    );  
    GO  
    ```  
  
2.  Aggiungere un indice per accelerare significativamente la query che popola la tabella **NewOrg** :  
  
    ```  
    CREATE CLUSTERED INDEX tmpind ON #Children(ManagerID, EmployeeID);  
    GO  
    ```  
  
### <a name="to-populate-the-neworg-table"></a>Per popolare la tabella NewOrg  
  
1.  Le query ricorsive impediscono le sottoquery con aggregazioni. In alternativa, popolare la tabella **#Children** con il codice seguente che usa il metodo [ROW_NUMBER()](../../t-sql/functions/row-number-transact-sql.md) per popolare la colonna **Num** :  
  
    ```  
    INSERT #Children (EmployeeID, ManagerID, Num)  
    SELECT EmployeeID, ManagerID,  
      ROW_NUMBER() OVER (PARTITION BY ManagerID ORDER BY ManagerID)   
    FROM EmployeeDemo  
    GO  
  
    ```  
  
2.  Rivedere la tabella **#Children** . Si noti in che modo la colonna **Num** contiene i numeri sequenziali per ogni responsabile.  
  
    ```  
    SELECT * FROM #Children ORDER BY ManagerID, Num  
    GO  
  
    ```  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    `EmployeeID ManagerID Num`  
  
    `---------- --------- ---`  
  
    `1        NULL       1`  
  
    `2         1         1`  
  
    `3         1         2`  
  
    `4         2         1`  
  
    `5         2         2`  
  
    `6         2         3`  
  
    `7         3         1`  
  
    `8         3         2`  
  
    `9         4         1`  
  
    `10        4         2`  
  
3.  Popolare la tabella **NewOrg** . Usare i metodi GetRoot e ToString per concatenare i valori **Num** nel formato **hierarchyid** , quindi aggiornare la colonna **OrgNode** con i valori di gerarchia risultanti:  
  
    ```  
    WITH paths(path, EmployeeID)   
    AS (  
    -- This section provides the value for the root of the hierarchy  
    SELECT hierarchyid::GetRoot() AS OrgNode, EmployeeID   
    FROM #Children AS C   
    WHERE ManagerID IS NULL   
  
    UNION ALL   
    -- This section provides values for all nodes except the root  
    SELECT   
    CAST(p.path.ToString() + CAST(C.Num AS varchar(30)) + '/' AS hierarchyid),   
    C.EmployeeID  
    FROM #Children AS C   
    JOIN paths AS p   
       ON C.ManagerID = P.EmployeeID   
    )  
    INSERT NewOrg (OrgNode, O.EmployeeID, O.LoginID, O.ManagerID)  
    SELECT P.path, O.EmployeeID, O.LoginID, O.ManagerID  
    FROM EmployeeDemo AS O   
    JOIN Paths AS P   
       ON O.EmployeeID = P.EmployeeID  
    GO  
  
    ```  
  
4.  Una colonna **hierarchyid** risulta più comprensibile quando viene convertita in un formato carattere. Rivedere i dati nella tabella **NewOrg** eseguendo il codice seguente che contiene due rappresentazioni della colonna **OrgNode** :  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode, *   
    FROM NewOrg   
    ORDER BY LogicalNode;  
    GO  
  
    ```  
  
    La colonna **LogicalNode** converte la colonna **hierarchyid** in un formato di testo più leggibile che rappresenta la gerarchia. Nelle attività rimanenti, verrà usato il metodo `ToString()` per mostrare il formato logico delle colonne **hierarchyid** .  
  
5.  Eliminare la tabella temporanea che non risulta più essere necessaria:  
  
    ```  
    DROP TABLE #Children  
    GO  
    ```  
  
L'attività successiva creerà indici per supportare la struttura gerarchica.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Ottimizzazione della tabella NewOrg](../../relational-databases/tables/lesson-1-3-optimizing-the-neworg-table.md)  
  
  
  
