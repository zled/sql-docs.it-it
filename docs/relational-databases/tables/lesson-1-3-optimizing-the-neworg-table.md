---
title: Ottimizzazione della tabella NewOrg | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- optimizing tables
ms.assetid: 89ff6d37-94c0-4773-8be9-dde943fff023
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 39a6587d88d14f9ac1950f7e1f6896258860b452
ms.sourcegitcommit: d6881107b51e1afe09c2d8b88b98d075589377de
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="lesson-1-3---optimizing-the-neworg-table"></a>Lezione 1-3: Ottimizzazione della tabella NewOrg
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
La tabella **NewOrd** creata nell'attività [Popolamento di una tabella con dati gerarchici esistenti](../../relational-databases/tables/lesson-1-2-populating-a-table-with-existing-hierarchical-data.md) contiene tutte le informazioni sul personale e rappresenta la struttura gerarchica usando un tipo di dati **hierarchyid** . Questa attività aggiunge indici nuovi per supportare ricerche nella colonna **hierarchyid** .  
  
## <a name="clustered-index"></a>Indice cluster  
La colonna **hierarchyid** (**OrgNode**) è la chiave primaria della tabella **NewOrg** . Quando la tabella è stata creata, conteneva un indice cluster denominato **PK_NewOrg_OrgNode** per applicare l'univocità della colonna **OrgNode** . Questo indice cluster supporta anche una ricerca in profondità nella tabella.  
  
## <a name="nonclustered-index"></a>Indice non cluster  
Questo passaggio crea due indici non cluster per supportare le ricerche tipiche.  
  
#### <a name="to-index-the-neworg-table-for-efficient-searches"></a>Per indicizzare la tabella NewOrg per eseguire ricerche efficienti  
  
1.  Per facilitare le query allo stesso livello nella gerarchia, usare il metodo [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) per creare una colonna calcolata contenente il livello della gerarchia. Quindi, creare un indice composto nel livello e **Hierarchyid**. Eseguire il codice seguente per creare la colonna calcolata e l'indice breadth-first:  
  
    ```  
    ALTER TABLE HumanResources.NewOrg   
       ADD H_Level AS OrgNode.GetLevel() ;  
    CREATE UNIQUE INDEX EmpBFInd   
       ON HumanResources.NewOrg(H_Level, OrgNode) ;  
    GO  
    ```  
  
2.  Creare un indice univoco nella colonna **EmployeeID** . Si tratta della ricerca singleton tradizionale di un solo dipendente in base al numero **EmployeeID** . Eseguire il codice seguente per creare un indice in **EmployeeID**:  
  
    ```  
    CREATE UNIQUE INDEX EmpIDs_unq ON HumanResources.NewOrg(EmployeeID) ;  
    GO
    ```  
  
3.  Eseguire il codice seguente per recuperare i dati dalla tabella nell'ordine di ognuno dei tre indici:  
  
    ```  
    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID  
    FROM HumanResources.NewOrg   
    ORDER BY OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY H_Level, OrgNode;  

    SELECT OrgNode.ToString() AS LogicalNode,  
    OrgNode, H_Level, EmployeeID, LoginID   
    FROM HumanResources.NewOrg   
    ORDER BY EmployeeID;  
    GO  
    ```  
  
4.  Confrontare i set di risultati per visualizzare il modo in cui l'ordine viene archiviato in ogni tipo di indice. Seguono solo le prime quattro righe di ogni output.  
  
    [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
    Indice depth-first: i record relativi ai dipendenti vengono archiviati accanto al responsabile.  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    ```

    **Indice EmployeeID**-first: le righe vengono archiviate nella sequenza di **EmployeeID**.  

    ```
    LogicalNode OrgNode H_Level EmployeeID  LoginID
    /   0x  0   1   adventure-works\ken0
    /1/ 0x58    1   2   adventure-works\terri0
    /1/1/   0x5AC0  2   3   adventure-works\roberto0
    /1/1/1/ 0x5AD6  3   4   adventure-works\rob0
    /1/1/2/ 0x5ADA  3   5   adventure-works\gail0
    /1/1/3/ 0x5ADE  3   6   adventure-works\jossef0
    /1/1/4/ 0x5AE1  3   7   adventure-works\dylan0
    /1/1/4/1/   0x5AE158    4   8   adventure-works\diane1
    /1/1/4/2/   0x5AE168    4   9   adventure-works\gigi0
    /1/1/4/3/   0x5AE178    4   10  adventure-works\michael6
    /1/1/5/ 0x5AE3  3   11  adventure-works\ovidiu0
    /1/1/5/1/   0x5AE358    4   12  adventure-works\thierry0
    ```
  
> [!NOTE]  
> Per i diagrammi che indicano la differenza tra un indice depth-first e un indice breadth-first, vedere [Dati gerarchici &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md).  
  
#### <a name="to-drop-the-unnecessary-columns"></a>Per eliminare le colonne non necessarie  
  
1.  La colonna **ManagerID** rappresenta la relazione dipendente/responsabile che ora è rappresentata dalla colonna **OrgNode** . Se le altre applicazioni non richiedono la colonna **ManagerID** , si consiglia di eliminarla usando l'istruzione seguente:  
  
    ```  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN ManagerID ;  
    GO  
    ```  
  
2.  La colonna **EmployeeID** è anche ridondante. La colonna **OrgNode** identifica in modo univoco ogni dipendente. Se le altre applicazioni non richiedono la colonna **EmployeeID** , eliminare l'indice e successivamente la colonna usando il codice seguente:  
  
    ```  
    DROP INDEX EmpIDs_unq ON HumanResources.NewOrg ;  
    ALTER TABLE HumanResources.NewOrg DROP COLUMN EmployeeID ;  
    GO  
    ```  
  
#### <a name="to-replace-the-original-table-with-the-new-table"></a>Per sostituire la tabella originale con la tabella nuova  
  
1.  Se la tabella originale contiene vincoli o indici aggiuntivi, aggiungerli alla tabella **NewOrg** .  
  
2.  Sostituire la vecchia colonna **EmployeeDemo** con la nuova tabella. Eseguire il codice seguente per rilasciare la vecchia tabella e successivamente rinominare la tabella nuova con il nome vecchio:  
  
    ```  
    DROP TABLE HumanResources.EmployeeDemo ;  
    GO  
    sp_rename 'HumanResources.NewOrg', 'EmployeeDemo' ;  
    GO  
    ```  
  
3.  Eseguire il codice seguente per esaminare la tabella finale:  
  
    ```  
    SELECT * FROM HumanResources.EmployeeDemo ;  
    ```  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Riepilogo: Conversione di una tabella in una struttura gerarchica](../../relational-databases/tables/lesson-1-4-summary-converting-a-table-to-a-hierarchical-structure.md)  
  
  
  
