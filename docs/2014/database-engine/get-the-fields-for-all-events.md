---
title: Recuperare i campi per tutti gli eventi | Documenti Microsoft
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
- extended events [SQL Server], getting fields
- xe
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fac62e2160086d920e3e73e770eaaf1cc82e0b88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36167511"
---
# <a name="get-the-fields-for-all-events"></a>Recuperare i campi per tutti gli eventi
  Il completamento di questa attività richiede l'utilizzo dell'editor di query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Al termine delle istruzioni in questa procedura, nella scheda **Results** dell'editor di query vengono visualizzate le colonne seguenti:  
  
-   package_name  
  
-   event_name  
  
-   event_field  
  
-   field_type  
  
-   column_type  
  
 È possibile utilizzare le informazioni precedenti durante la configurazione di sessioni eventi che utilizzano la destinazione di bucket. Per ulteriori informazioni, vedere [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Prima di creare una sessione Eventi estesi di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , è utile ottenere informazioni sui campi associati agli eventi.  
  
## <a name="to-get-the-fields-for-all-events-using-query-editor"></a>Per recuperare i campi per tutti gli eventi tramite l'editor di query  
  
-   Nell'editor di query eseguire le istruzioni indicate di seguito.  
  
    ```  
    select p.name package_name, o.name event_name, c.name event_field, c.type_name field_type, c.column_type column_type  
    from sys.dm_xe_objects o  
    join sys.dm_xe_packages p  
          on o.package_guid = p.guid  
    join sys.dm_xe_object_columns c  
          on o.name = c.object_name  
    where o.object_type = 'event'  
    order by package_name, event_name  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
