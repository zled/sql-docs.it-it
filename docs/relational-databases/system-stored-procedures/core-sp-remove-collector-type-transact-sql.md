---
title: core.sp_remove_collector_type (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_remove_collector_type
- sp_remove_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- core.sp_remove_collector_type stored procedure
- management data warehouse, data collector stored procedures
- sp_remove_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 88ceba25-e41a-405f-a416-bb68918a0024
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef7aa35eea529857072492d4b1d80ddf92c69ef6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47726869"
---
# <a name="corespremovecollectortype-transact-sql"></a>core.sp_remove_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove una voce dalla vista core.supported_collector_types nel database del data warehouse di gestione. La procedura deve essere eseguita nel contesto del database del data warehouse di gestione.  
  
 La vista core.supported_collector_types include i tipi di agente di raccolta registrati che possono caricare i dati nel data warehouse di gestione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
core.sp_remove_collector_type [ @collector_type_uid = ] 'collector_type_uid'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @collector_type_uid =] '*collector_type_uid*'  
 GUID per il tipo agente di raccolta. *collector_type_uid* viene **uniqueidentifier**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="permissions"></a>Permissions  
 Richiede l'appartenenza al **mdw_admin** (con autorizzazione EXECUTE) ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimosso il tipo di agente di raccolta query T-SQL generico dalla vista core.supported_collector_types.  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @RC int;  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = (SELECT collector_type_uid FROM msdb.dbo.syscollector_collector_types WHERE name = N'Generic T-SQL Query Collector Type');  
EXECUTE @RC = core.sp_remove_collector_type @collector_type_uid;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Data warehouse di gestione](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
