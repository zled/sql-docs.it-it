---
title: "Informazioni sulla proprietà dei diagrammi di database (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8c5c09fbf0c7255509e7a34726866f4e5328c4de
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="understand-database-diagram-ownership-visual-database-tools"></a>Informazioni sulla proprietà dei diagrammi di database (Visual Database Tools)
Per poter utilizzare la Progettazione diagrammi di database, è necessario che un membro del ruolo db_owner (un ruolo dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ) ne effettui preventivamente la configurazione per il controllo dell'accesso ai diagrammi. Ciascun diagramma ha un solo proprietario, ovvero l'utente che lo ha creato. Per altre informazioni sull'impostazione dei diagrammi, vedere [Impostazione di Progettazione diagrammi di database (Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md).  
  
In relazione alla proprietà dei diagrammi, tenere presente quanto segue:  
  
-   Benché un diagramma possa essere creato da qualsiasi utente che dispone di accesso a un database, potrà essere visualizzato solo dall'utente che lo ha creato e dai membri del ruolo db_owner.  
  
-   La proprietà dei diagrammi può essere trasferita solo ai membri del ruolo db_owner e soltanto se il proprietario precedente è stato rimosso dal database.  
  
-   Se il proprietario di un diagramma viene rimosso dal database, il diagramma rimarrà all'interno del database finché un membro del ruolo db_owner non tenterà di aprirlo. A questo punto, il membro del ruolo db_owner potrà scegliere di subentrare come proprietario del diagramma.  
  
## <a name="see-also"></a>Vedere anche  
[Utilizzare diagrammi di database (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[Impostazione di Progettazione diagrammi di database (Visual Database Tools)](../../ssms/visual-db-tools/set-up-database-diagram-designer-visual-database-tools.md)  
  
