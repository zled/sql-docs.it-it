---
title: Creazione di una tabella tramite il tipo di dati hierarchyid | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
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
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a34fde9a22dd93ae67d376ca275117484adab430
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-2-1---creating-a-table-using-the-hierarchyid-data-type"></a>Lezione 2-1: Creazione di una tabella tramite il tipo di dati hierarchyid
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
Nell'esempio seguente viene creata una tabella denominata EmployeeOrg che include i dati del dipendente e la gerarchia del report. L'esempio crea la tabella nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , ma questo è facoltativo. Per mantenere l'esempio semplice, in questa tabella sono incluse solo cinque colonne:  
  
-   OrgNode è una colonna **hierarchyid** che archivia la relazione gerarchica.  
  
-   OrgLevel è una colonna calcolata in base alla colonna OrgNode che archivia il livello di ciascun nodo nella gerarchia. Verrà utilizzata per un indice breadth-first.  
  
-   Il numero di identificazione tipico del dipendente, utilizzato per applicazioni quali libro paga, è contenuto in EmployeeID. Nello sviluppo di nuove applicazioni, le applicazioni possono utilizzare la colonna OrgNode mentre la colonna separata EmployeeID non è necessaria.  
  
-   EmpName contiene il nome del dipendente.  
  
-   Title contiene la posizione del dipendente.  
  
### <a name="to-create-the-employeeorg-table"></a>Per creare la tabella EmployeeOrg  
  
1.  Nella finestra dell'editor di query eseguire il codice seguente per creare la tabella `EmployeeOrg` . Specificando la colonna `OrgNode` come chiave primaria con un indice cluster, verrà creato un indice depth-first:  
  
    ```  
    USE AdventureWorks2012 ;  
    GO  
    CREATE TABLE HumanResources.EmployeeOrg  
    (  
       OrgNode hierarchyid PRIMARY KEY CLUSTERED,  
       OrgLevel AS OrgNode.GetLevel(),  
       EmployeeID int UNIQUE NOT NULL,  
       EmpName varchar(20) NOT NULL,  
       Title varchar(20) NULL  
    ) ;  
    GO  
    ```  
  
2.  Eseguire il codice riportato di seguito per creare un indice composto per le colonne `OrgLevel` e `OrgNode` al fine di supportare ricerche breadth-first efficienti:  
  
    ```  
    CREATE UNIQUE INDEX EmployeeOrgNc1   
    ON HumanResources.EmployeeOrg(OrgLevel, OrgNode) ;  
    GO  
    ```  
  
La tabella è ora pronta per i dati. La prossima attività popolerà la tabella utilizzando metodi gerarchici.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Popolamento di una tabella gerarchica utilizzando metodi gerarchici](../../relational-databases/tables/lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  
  
