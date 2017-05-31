---
title: Impostare Progettazione diagrammi di database (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9afcf20de2220aee5d9be2763a0b274ec738e48c
ms.contentlocale: it-it
ms.lasthandoff: 04/11/2017

---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Impostazione di Progettazione diagrammi di database (Visual Database Tools)
Per usare Progettazione diagrammi di database, è necessario che un membro del ruolo **proprietario_database** ne effettui preventivamente la configurazione per il controllo dell'accesso ai diagrammi.  
  
### <a name="to-set-up-database-diagramming"></a>Per impostare i diagrammi di database  
  
1.  In Esplora oggetti espandere un nodo di database.  
  
2.  Espandere il nodo dei diagrammi di database al di sotto della connessione al database.  
  
3.  Quando viene chiesto se si intende configurare i diagrammi di database, scegliere **Sì** .  
  
    > [!NOTE]  
    > Nel database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] verranno create la tabella del diagramma di database, le stored procedure di sistema e una funzione di sistema.  
  
4.  Tramite Visual Studio verranno creati i seguenti oggetti nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
    1.  Tabella sysdiagrams  
  
    2.  Stored procedure sp_alterdiagram  
  
    3.  Stored procedure sp_creatediagram  
  
    4.  Stored procedure sp_dropdiagram  
  
    5.  Stored procedure sp_renamediagram  
  
    6.  Funzione fn_diagramobjects  
  
    7.  Stored procedure sp_helpdiagrams  
  
    8.  Stored procedure sp_helpdiagramsdefinition  
  
    9. Stored procedure sp_upgraddiagrams  
  
## <a name="see-also"></a>Vedere anche  
[Informazioni sulla proprietà dei diagrammi di database &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/understand-database-diagram-ownership-visual-database-tools.md)  
[Aggiornamento di diagrammi di database delle precedenti edizioni &amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
[ALTER AUTHORIZATION (Transact-SQL)](http://msdn.microsoft.com/en-us/8c805ae2-91ed-4133-96f6-9835c908f373)  
  

