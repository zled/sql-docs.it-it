---
title: Creazione di una tabella tramite il tipo di dati hierarchyid | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HierarchyID
ms.assetid: 0d1f361f-336c-4571-99d1-f4813b2d9fc4
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ecf8817fb0c153298a53ba1be4c49606c0200a93
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062820"
---
# <a name="creating-a-table-using-the-hierarchyid-data-type"></a>Creazione di una tabella utilizzando il tipo di dati hierarchyid
  Nell'esempio seguente viene creata una tabella denominata EmployeeOrg che include i dati del dipendente e la gerarchia del report. L'esempio crea la tabella nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , ma questo è facoltativo. Per mantenere l'esempio semplice, in questa tabella sono incluse solo cinque colonne:  
  
-   OrgNode è una colonna `hierarchyid` che archivia la relazione gerarchica.  
  
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
 [Popolamento di una tabella gerarchica utilizzando metodi gerarchici](lesson-2-2-populating-a-hierarchical-table-using-hierarchical-methods.md)  
  
  