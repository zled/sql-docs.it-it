---
title: "Informazioni sulla proprietà dei diagrammi di database (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vdt.diagnostic.CannotOpenWithInvalidOwner
helpviewer_keywords:
- diagrams [SQL Server], ownership
- database diagrams [SQL Server], ownership
- owners [SQL Server], database diagrams
ms.assetid: 4a27a48e-c4ef-4017-82b8-0cac4d0bbcac
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 685a25b7968b24e729f53a943276d8cdaad33b7f
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Informazioni sulla proprietà dei diagrammi di database (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Per poter usare Progettazione diagrammi di database, è necessario che un membro del ruolo db_owner (un ruolo dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]) ne effettui preventivamente la configurazione per il controllo dell'accesso ai diagrammi. Ciascun diagramma ha un solo proprietario, ovvero l'utente che lo ha creato. Per altre informazioni sull'impostazione dei diagrammi, vedere [Impostazione di Progettazione diagrammi di database (Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md).  
  
In relazione alla proprietà dei diagrammi, tenere presente quanto segue:  
  
-   Benché un diagramma possa essere creato da qualsiasi utente che dispone di accesso a un database, potrà essere visualizzato solo dall'utente che lo ha creato e dai membri del ruolo db_owner.  
  
-   La proprietà dei diagrammi può essere trasferita solo ai membri del ruolo db_owner e soltanto se il proprietario precedente è stato rimosso dal database.  
  
-   Se il proprietario di un diagramma viene rimosso dal database, il diagramma rimarrà all'interno del database finché un membro del ruolo db_owner non tenterà di aprirlo. A questo punto, il membro del ruolo db_owner potrà scegliere di subentrare come proprietario del diagramma.  
  
## <a name="see-also"></a>Vedere anche  
[Usare diagrammi di database (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Impostazione di Progettazione diagrammi di database (Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)  
  
