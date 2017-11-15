---
title: Esecuzione di query su una tabella gerarchica tramite metodi gerarchici | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
helpviewer_keywords: HierarchyID
ms.assetid: 3b4f7dae-65b5-4d8d-8641-87aba9aa692d
caps.latest.revision: "18"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c421750c7654ae0993fea523ebceaa2e2dd49ee3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="lesson-2-3---querying-a-hierarchical-table-using-hierarchy-methods"></a>Lezione 2-3: Esecuzione di query su una tabella gerarchica tramite metodi gerarchici
Ora che la tabella HumanResources.EmployeeOrg è completamente popolata, in questa attività verrà illustrato come eseguire una query sulla gerarchia utilizzando alcuni dei metodi gerarchici.  
  
### <a name="to-find-subordinate-nodes"></a>Per trovare nodi subordinati  
  
1.  Sariya ha un dipendente subordinato. Per eseguire una query sui subalterni di Sariya, eseguire la query seguente che usa il metodo [IsDescendantOf](../../t-sql/data-types/isdescendantof-database-engine.md) :  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.IsDescendantOf(@CurrentEmployee ) = 1 ;  
    ```  
  
    I risultati indicano sia Sariya sia Wanida. Sariya viene indicata perché rappresenta l'elemento discendente al livello 0. Wanida rappresenta l'elemento discendente al livello 1.  
  
2.  È anche possibile eseguire una query per ottenere tali informazioni usando il metodo [GetAncestor](../../t-sql/data-types/getancestor-database-engine.md) . `GetAncestor` accetta un argomento per il livello che si tenta di restituire. Poiché Wanida è un livello sotto Sariya, utilizzare `GetAncestor(1)` come dimostrato nel codice seguente:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 46 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(1) = @CurrentEmployee  
    ```  
  
    Questa volta nei risultati viene indicata solo Wanida.  
  
3.  Ora impostare `@CurrentEmployee` su David (EmployeeID 6) e il livello su 2. Eseguire quanto segue per restituire anche Wanida:  
  
    ```  
    DECLARE @CurrentEmployee hierarchyid  
  
    SELECT @CurrentEmployee = OrgNode  
    FROM HumanResources.EmployeeOrg  
    WHERE EmployeeID = 6 ;  
  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode.GetAncestor(2) = @CurrentEmployee  
    ```  
  
    Questa volta, due livelli più in basso, viene indicata anche Mary che riporta a David.  
  
### <a name="to-use-getroot-and-getlevel"></a>Utilizzo di GetRoot e GetLevel  
  
1.  Con il crescere della gerarchia diventa più difficile determinare la posizione dei membri nella stessa. Usare il metodo [GetLevel](../../t-sql/data-types/getlevel-database-engine.md) per scoprire quanti livelli ci sono al di sotto di ogni riga della gerarchia. Eseguire il codice seguente per visualizzare i livelli di tutte le righe:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode,   
    OrgNode.GetLevel() AS EmpLevel, *  
    FROM HumanResources.EmployeeOrg ;  
    GO  
  
    ```  
  
2.  Usare il metodo [GetRoot](../../t-sql/data-types/getroot-database-engine.md) per cercare il nodo radice della gerarchia. Il codice seguente restituisce la singola riga che è la radice:  
  
    ```  
    SELECT OrgNode.ToString() AS Text_OrgNode, *  
    FROM HumanResources.EmployeeOrg  
    WHERE OrgNode = hierarchyid::GetRoot() ;  
    GO  
  
    ```  
  
L'attività successiva riorganizzerà la gerarchia.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Riordinamento di dati in una tabella gerarchica utilizzando metodi gerarchici](../../relational-databases/tables/lesson-2-4-reordering-data-in-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
  
