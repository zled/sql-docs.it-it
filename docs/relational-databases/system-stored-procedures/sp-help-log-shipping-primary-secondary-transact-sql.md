---
title: sp_help_log_shipping_primary_secondary (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_primary_secondary
- sp_help_log_shipping_primary_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_primary_secondary
ms.assetid: bc0044b4-7831-4ff9-8856-825c76aa9893
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce048ac74fb8aeccb209c2d0b72273a773c92170
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sphelplogshippingprimarysecondary-transact-sql"></a>sp_help_log_shipping_primary_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa stored procedure restituisce informazioni su tutti i database secondari di un determinato database primario.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_log_shipping_primary_secondary  
[ @primary_database = ] 'primary_database'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@primary_database =** ] '*primary_database*'  
 Nome del database sul server primario. *primary_database* viene **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|**secondary_server**|Il nome dell'istanza secondaria del [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] nella configurazione di log shipping.|  
|**secondary_database**|Nome del database secondario nella configurazione di log shipping.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_help_log_shipping_primary_secondary** deve essere eseguita la **master** database nel server primario.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene illustrato l'utilizzo **sp_help_log_shipping_primary_secondary** per recuperare un elenco di database secondario database associati dal database primario [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXECUTE master.dbo.sp_help_log_shipping_primary_secondary @primary_database=N'AdventureWorks';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
