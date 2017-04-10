---
title: "Riordinamento di dati in una tabella gerarchica utilizzando metodi gerarchici | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
helpviewer_keywords: 
  - "HierarchyID"
ms.assetid: 7b8064c7-62c6-488d-84d2-57a5828fb907
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Riordinamento di dati in una tabella gerarchica utilizzando metodi gerarchici
La riorganizzazione di una gerarchia è un'attività di manutenzione comune. In questa attività verrà usata un'istruzione UPDATE con il metodo [GetReparentedValue](../../t-sql/data-types/getreparentedvalue-database-engine.md) per spostare innanzitutto una singola riga in un percorso nuovo della gerarchia. Verrà quindi spostato un sottoalbero intero in un nuovo percorso.  
  
Il metodo `GetReparentedValue` utilizza due argomenti. Nel primo argomento viene descritta la parte della gerarchia da modificare. Ad esempio, se una gerarchia è **/1/4/2/3/** e si vuole modificare la sezione **/1/4/**, la gerarchia diventa **/2/1/2/3/**, lasciando gli ultimi due nodi (**2/3/**) inalterati, è necessario specificare i nodi modificati (**/1/4/**) come primo argomento. Il secondo argomento specifica il nuovo livello della gerarchia, nell'esempio **/2/1/**. Non è necessario che i due argomenti contengano lo stesso numero di livelli.  
  
### Per spostare una sola riga in un percorso nuovo nella gerarchia  
  
1.  Attualmente Wanida riporta a Sariya. In questa procedura, si sposta Wanida dal nodo corrente **/1/1/,** in modo che riporti a Jill. Il suo nodo nuovo diventerà **/3/1/** e **/1/** diventa il primo argomento, mentre **/3/** diventa il secondo argomento. Gli argomenti corrispondono ai valori **OrgNode** di Sariya e Jill. Eseguire il codice seguente per spostare Wanida dall'organizzazione di Sariya a quella di Jill:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 269 ;   
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 46 ;   
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
      WHERE EmployeeID = 119 ;   
  
    UPDATE HumanResources.EmployeeOrg  
    SET OrgNode = @CurrentEmployee. GetReparentedValue(@OldParent, @NewParent)   
    WHERE OrgNode = @CurrentEmployee ;  
    GO  
    ```  
  
2.  Eseguire il codice seguente per visualizzare il risultato:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
    Wanida ora è al nodo **/3/1/**.  
  
### Per riorganizzare una sezione di una gerarchia  
  
1.  Per dimostrare come spostare contemporaneamente un numero maggiore di persone, eseguire innanzitutto il codice seguente per aggiungere un report del tirocinante a Wanida:  
  
    ```  
    EXEC AddEmp 269, 291, 'Kevin', 'Marketing Intern'  ;  
    GO  
    ```  
  
2.  Ora Kevin riporta a Wanida che riporta a Jill che riporta a David. Questo significa che Kevin è al livello **/3/1/1/**. Per spostare tutti i subalterni di Jill a un nuovo responsabile, verranno aggiornati tutti i nodi che hanno **/3/** in **OrgNode** con un nuovo valore. Eseguire il codice seguente per aggiornare Wanida in modo che riporti a Sariya, ma lasciando che Kevin riporti a Wanida:  
  
    ```  
    DECLARE @OldParent hierarchyid, @NewParent hierarchyid  
    SELECT @OldParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 119 ; -- Jill  
    SELECT @NewParent = OrgNode FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ; -- Sariya  
    DECLARE children_cursor CURSOR FOR  
    SELECT OrgNode FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @OldParent;  
    DECLARE @ChildId hierarchyid;  
    OPEN children_cursor  
    FETCH NEXT FROM children_cursor INTO @ChildId;  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
    START:  
        DECLARE @NewId hierarchyid;  
        SELECT @NewId = @NewParent.GetDescendant(MAX(OrgNode), NULL)  
        FROM HumanResources.EmployeeOrg WHERE OrgNode.GetAncestor(1) = @NewParent;  
  
        UPDATE HumanResources.EmployeeOrg  
        SET OrgNode = OrgNode.GetReparentedValue(@ChildId, @NewId)  
        WHERE OrgNode.IsDescendantOf(@ChildId) = 1;  
        IF @@error <> 0 GOTO START -- On error, retry  
            FETCH NEXT FROM children_cursor INTO @ChildId;  
    END  
    CLOSE children_cursor;  
    DEALLOCATE children_cursor;  
  
    ```  
  
3.  Eseguire il codice seguente per visualizzare il risultato:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode, OrgLevel, EmployeeID, EmpName, Title   
    FROM HumanResources.EmployeeOrg ;  
    GO  
    ```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Text_OrgNode OrgNode OrgLevel EmployeeID EmpName Title  
------------ ------- -------- ---------- ------- -----------------  
/            Ox      0        6          David   Marketing Manager  
/1/          0x58    1        46         Sariya  Marketing Specialist  
/1/1/        0x5AC0  2        269        Wanida  Marketing Assistant  
/1/1//2      0x5AD0  3        291        Kevin   Marketing Intern  
/2/          0x68    1        271        John    Marketing Specialist  
/2/1/        0x6AC0  2        272        Mary    Marketing Assistant  
/3/          0x78    1        119        Jill    Marketing Specialist  
```  
  
L'intero albero organizzativo che riportava a Jill (Wanida e Kevin) ora riporta a Sariya.  
  
Per riorganizzare una sezione di una gerarchia tramite una stored procedure, vedere la sezione [Spostamento di sottoalberi](../../relational-databases/hierarchical-data-sql-server.md#BKMK_MovingSubtrees).  
  
## Attività successiva della lezione  
[Riepilogo: Gestione di dati in una tabella gerarchica](../../relational-databases/tables/summary-managing-data-in-a-hierarchical-table.md)  
  
  
  
