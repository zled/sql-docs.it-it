---
title: Gerarchia delle autorizzazioni (motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.server.permissions.f1--May use common.permissions
helpviewer_keywords:
- security [SQL Server], denying access
- hierarchies [SQL Server], permissions
- securables [SQL Server]
- security [SQL Server], permissions
- permissions [SQL Server], hierarchy
- security [SQL Server], granting access
ms.assetid: f6d20a55-ef03-4e14-85f9-009902889866
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: bd63fe14bf1f21196a727e44596fae5682b51117
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247951"
---
# <a name="permissions-hierarchy-database-engine"></a>Gerarchia delle autorizzazioni (Motore di database)
  [!INCLUDE[ssDE](../../../includes/ssde-md.md)] gestisce una raccolta gerarchica di entità che possono essere protette attraverso l'uso di autorizzazioni. Queste entità sono denominate *entità a sicurezza diretta*. Le entità a protezione diretta più significative sono server e database, ma è possibile impostare autorizzazione distinte a un livello più specifico. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] regola le azioni delle entità sulle entità a protezione diretta verificando che siano state concesse le autorizzazioni corrette.  
  
 Nella figura seguente vengono illustrate le relazioni esistenti tra le gerarchie di autorizzazioni di [!INCLUDE[ssDE](../../../includes/ssde-md.md)] .  
  
 ![Diagramma delle gerarchie di autorizzazioni del motore di database](../../database-engine/media/wj-security-layers.gif "Diagramma delle gerarchie di autorizzazioni del motore di database")  
  
## <a name="chart-of-sql-server-permissions"></a>Grafico delle autorizzazioni di SQL Server  
 Per un'anteprima di grandi dimensioni di tutte le autorizzazioni del [!INCLUDE[ssDE](../../../includes/ssde-md.md)] in formato pdf, vedere [http://go.microsoft.com/fwlink/?LinkId=229142](http://go.microsoft.com/fwlink/?LinkId=229142).  
  
## <a name="working-with-permissions"></a>Utilizzo delle autorizzazioni  
 Le autorizzazioni possono essere manipolate attraverso le ben note query GRANT, DENY e REVOKE [!INCLUDE[tsql](../../includes/tsql-md.md)] . Le informazioni sulle autorizzazioni sono visualizzate nelle viste di catalogo [sys.server_permissions](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql) e [sys.database_permissions](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql) . Le funzioni predefinite offrono inoltre supporto per query sulle informazioni relative alle autorizzazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza di SQL Server](securing-sql-server.md)   
 [Autorizzazioni &#40;motore di database&#41;](permissions-database-engine.md)   
 [Securables](securables.md)   
 [Entità &#40;motore di database&#41;](authentication-access/principals-database-engine.md)   
 [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)   
 [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql)   
 [DENY &#40;Transact-SQL&#41;](/sql/t-sql/statements/deny-transact-sql)   
 [HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/has-perms-by-name-transact-sql)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql)   
 [sys.server_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-permissions-transact-sql)   
 [sys.database_permissions &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-permissions-transact-sql)  
  
  
