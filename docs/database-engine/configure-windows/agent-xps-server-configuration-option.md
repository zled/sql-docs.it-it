---
title: Opzione di configurazione del server Agent XPs | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 34863e78d2210b8c5860258dd5ade1f7aeb241c2
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="agent-xps-server-configuration-option"></a>Opzione di configurazione del server Agent XPs
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  L'opzione **Agent XPs** consente di abilitare le stored procedure estese del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nel server. Se questa opzione non è attivata, il nodo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent non sarà disponibile in Esplora oggetti di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 Quando si utilizza lo strumento [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per avviare il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, le stored procedure estese vengono abilitate automaticamente. Per ulteriori informazioni, vedere [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] In Esplora oggetti il nodo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent non viene visualizzato a meno che le stored procedure estese non vengano abilitate indipendentemente dallo stato del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
 I valori possibili sono:  
  
-   **0**, che indica che le stored procedure estese di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent non sono disponibili e corrisponde al valore predefinito.  
  
-   **1**, che indica che le stored procedure estese di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sono disponibili.  
  
 L'impostazione diventa effettiva immediatamente e non richiede l'arresto e il riavvio del server.  
  
## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata l'attivazione delle stored procedure estese di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  

1. Connettersi al motore di database da Microsoft SQL Server Management Studio.

2.  Dalla barra Standard fare clic su **Nuova query**.

3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. 
  
```tsql 
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Automatizzazione delle attività amministrative &#40;SQL Server Agent&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)   
 [Avvio, arresto o sospensione del servizio SQL Server Agent](http://msdn.microsoft.com/library/c95a9759-dd30-4ab6-9ab0-087bb3bfb97c)  
  
  

