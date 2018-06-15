---
title: sp_delete_log_shipping_primary_database (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_log_shipping_primary_database
- sp_delete_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_primary_database
ms.assetid: cb1d5d00-2805-4d47-bd04-545232067345
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 76a1b1ac129d33866984eb7a0f428149e4e299a2
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33258716"
---
# <a name="spdeletelogshippingprimarydatabase-transact-sql"></a>sp_delete_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Questa stored procedure rimuove il log shipping del database primario, compreso il processo di backup, e la cronologia locale e remota. Utilizzare solo questa stored procedure dopo aver rimosso il database secondario tramite **sp_delete_log_shipping_primary_secondary**.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_delete_log_shipping_primary_database  
[ @database = ] 'database'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@database =** ] '*database*'  
 Nome del database primario per il log shipping. *database* viene **sysname**, non prevede alcun valore predefinito e non può essere NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_delete_log_shipping_primary_database** deve essere eseguita la **master** database nel server primario. Questa stored procedure esegue le operazioni seguenti:  
  
1.  Elimina il processo di backup per il database primario specificato.  
  
2.  Rimuove il record di monitoraggio locale in **log_shipping_monitor_primary** nel server primario.  
  
3.  Rimuove le voci corrispondenti in **log_shipping_monitor_history_detail** e **log_shipping_monitor_error_detail**.  
  
4.  Se il server di monitoraggio è diverso dal server primario, rimuove il record di monitoraggio in **log_shipping_monitor_primary** sul server di monitoraggio.  
  
5.  Rimuove le voci corrispondenti in **log_shipping_monitor_history_detail** e **log_shipping_monitor_error_detail** sul server di monitoraggio.  
  
6.  Rimuove la voce in **log_shipping_primary_databases** per il database primario.  
  
7.  Chiamate **sp_delete_log_shipping_alert_job** sul server di monitoraggio.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire questa procedura.  
  
## <a name="examples"></a>Esempi  
 In questo esempio viene illustrato l'utilizzo **sp_delete_log_shipping_primary_database** per eliminare il database primario **AdventureWorks2012**.  
  
```  
EXEC master.dbo.sp_delete_log_shipping_primary_database @database = N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping & #40; SQL Server & #41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
