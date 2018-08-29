---
title: sp_repltrans (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 827ff7056b25ea3984838b5a4993eea63738920b
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022606"
---
# <a name="sprepltrans-transact-sql"></a>sp_repltrans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un set di risultati che include tutte le transazioni del log delle transazioni del database di pubblicazione contrassegnate per la replica, ma non contrassegnate come distribuite. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_repltrans  
```  
  
## <a name="result-sets"></a>Set di risultati  
 **sp_repltrans** restituisce informazioni sul database di pubblicazione da cui viene eseguito, per consentire la visualizzazione delle transazioni non distribuite (quelle che rimangono nel log delle transazioni che non sono stati inviati per il Server di distribuzione). Il set di risultati include i numeri di sequenza del file di log del primo e dell'ultimo record per ogni transazione. **sp_repltrans** è simile a [sp_replcmds &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) ma non restituisce i comandi per le transazioni.  
  
## <a name="remarks"></a>Note  
 **sp_repltrans** viene utilizzata nella replica transazionale.  
  
 **sp_repltrans** non è supportata per non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o il **db_owner** ruolo predefinito del database possono eseguire **sp_repltrans**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
