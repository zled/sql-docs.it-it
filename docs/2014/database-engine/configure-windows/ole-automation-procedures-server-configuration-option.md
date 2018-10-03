---
title: Opzione di configurazione del server Ole Automation Procedures | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d8a01c5bf886006e2f4eb6a352ea7f2a7b43ac29
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056001"
---
# <a name="ole-automation-procedures-server-configuration-option"></a>Opzione di configurazione del server Ole Automation Procedures
  Utilizzare l'opzione `Ole Automation Procedures` per specificare se è possibile creare un'istanza degli oggetti di automazione OLE all'interno di batch [!INCLUDE[tsql](../../includes/tsql-md.md)]. Questa opzione può essere configurata usando anche la gestione basata su criteri o la stored procedure **sp_configure** . Per ulteriori informazioni, vedere [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
 Il `Ole Automation Procedures` opzione può essere impostata sui valori seguenti.  
  
 0  
 L'opzione Ole Automation Procedures è disabilitata. Impostazione predefinita per le nuove istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 1  
 L'opzione Ole Automation Procedures è abilitata.  
  
 Quando l'opzione Ole Automation Procedures è abilitata, l'ambiente di esecuzione condiviso OLE viene avviato mediante una chiamata a **sp_OACreate** .  
  
 Il valore corrente del `Ole Automation Procedures` opzione può essere visualizzata e modificata tramite il **sp_configure** stored procedure di sistema.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrata la procedura per la visualizzazione dell'impostazione corrente dell'opzione Ole Automation Procedures.  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 Nell'esempio seguente viene illustrata la procedura per l'abilitazione dell'opzione Ole Automation Procedures.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Configurazione superficie di attacco](../../relational-databases/security/surface-area-configuration.md)   
 [Opzioni di configurazione del server &#40;SQL Server&#41;](server-configuration-options-sql-server.md)  
  
  
