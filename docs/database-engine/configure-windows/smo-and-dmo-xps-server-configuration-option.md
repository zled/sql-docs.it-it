---
title: Opzioni di configurazione del server SMO e DMO XPs | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcd945ba-5d81-4124-9a2b-d87491c2a369
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ccd3457a8081eea7d57c9c3d673adf2b3fb6db07
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="smo-and-dmo-xps-server-configuration-option"></a>Opzioni di configurazione del server SMO e DMO XPs
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  L'opzione SMO and DMO XPs consente di abilitare le stored procedure estese SMO ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object) nel server.  
  
 Si noti che, a partire da [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], DMO è stato rimosso da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 I valori possibili sono illustrati nella tabella seguente:  
  
|Valore|Significato|  
|-----------|-------------|  
|0|Le stored procedure estese SMO non sono disponibili.|  
|1|Le stored procedure estese SMO sono disponibili. Impostazione predefinita.|  
  
 L'impostazione diventa immediatamente effettiva.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono abilitate le stored procedure estese SMO.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'SMO and DMO XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida alla programmazione di SQL Server Management Objects &#40;SMO&#41;](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md)  
  
  

