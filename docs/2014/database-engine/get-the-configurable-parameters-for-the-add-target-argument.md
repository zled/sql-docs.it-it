---
title: Ottenere i parametri configurabili per l'argomento ADD TARGET | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], ADD TARGET argument
- xe
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
caps.latest.revision: 14
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f7aa048d5596e756015b5755fec6d3b9968e922a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310331"
---
# <a name="get-the-configurable-parameters-for-the-add-target-argument"></a>Recuperare i parametri configurabili per l'argomento ADD TARGET
  Il completamento di questa attività richiede l'utilizzo dell'editor di query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Al termine delle istruzioni in questa procedura, nella scheda **Results** dell'editor di query vengono visualizzate le colonne seguenti:  
  
-   package_name  
  
-   target_name  
  
-   parameter_name  
  
-   parameter_type  
  
-   required  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
 Prima di creare una sessione degli eventi estesi di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , è utile individuare i parametri che è possibile impostare quando si utilizza l'argomento ADD TARGET in CREATE EVENT SESSION o ALTER EVENT SESSION.  
  
### <a name="to-get-the-configurable-parameters-for-the-add-target-argument-using-query-editor"></a>Per recuperare i parametri configurabili per l'argomento ADD TARGET tramite l'editor di query  
  
-   Nell'editor di query eseguire le istruzioni indicate di seguito.  
  
    ```  
    SELECT p.name package_name, o.name target_name, c.name parameter_name,   
    c.type_name parameter_type, CASE c.capabilities_desc WHEN 'mandatory' THEN 'yes' ELSE 'no' END   
    required   
    FROM sys.dm_xe_objects o JOIN sys.dm_xe_packages p ON o.package_guid = p.guid   
    JOIN sys.dm_xe_object_columns c ON o.name = c.object_name AND c.column_type = 'customizable'  
    WHERE o.object_type = 'target'   
    ORDER BY package_name, target_name, required DESC  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
