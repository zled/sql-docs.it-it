---
title: sys.sp_xtp_unbind_db_resource_pool (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_xtp_unbind_db_resource_pool_TSQL
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool_TSQL
- sys.sp_xtp_unbind_db_resource_pool
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool
ms.assetid: 695a796d-087e-4bc8-99d0-ddc342604c75
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 852d8db43c417d828678929f46ee28f12623a4af
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysspxtpunbinddbresourcepool-transact-sql"></a>sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Tramite questa procedura di sistema viene rimossa un'associazione esistente tra un database e un pool di risorse allo scopo di tenere traccia dell'utilizzo di memoria di [!INCLUDE[hek_2](../../includes/hek-2-md.md)].  Se attualmente non vi sono pool associati al database specificato, l'operazione viene completata. Quando il database non è associato, la memoria allocata in precedenza per gli oggetti ottimizzati per la memoria rimane allocata al pool di risorse precedente. È necessario riavviare il database per liberare la memoria allocata. Una volta annullata l'associazione tra un database e il pool di risorse, viene utilizzato il pool di risorse DEFAULT da parte dell'associazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
sys.sp_xtp_unbind_db_resource_pool 'database_name'  
```  
  
## <a name="arguments"></a>Argomenti  
 database_name  
 Nome di un database abilitato per [!INCLUDE[hek_2](../../includes/hek-2-md.md)] esistente.  
  
#### <a name="parameters"></a>Parametri  
  
## <a name="messages"></a>Messaggi  
 Se il database è associato a un pool di risorse denominato, la procedura viene eseguita correttamente. Tuttavia, è necessario riavviare il database per rendere effettivo l'annullamento dell'associazione.  
 Se non esiste alcuna associazione esistente per il database specificato, `sp_xtp_unbind_db_resource_pool` viene eseguita correttamente, ma viene visualizzato il messaggio informativo:  
  
```  
Msg 41374, Level 16, State 1, Procedure sp_xtp_unbind_db_resource_pool_internal, Line 140.  
Database 'Hekaton_DB' does not have a binding to a resource pool.  
  
```  
  
## <a name="example"></a>Esempio  
 Nel codice seguente viene annullata l'associazione tra il database Hekaton_DB e il pool di risorse [!INCLUDE[hek_2](../../includes/hek-2-md.md)] a cui è stata eseguita l'associazione.  Se Hekaton_DB non è attualmente associato a un pool di risorse di [!INCLUDE[hek_2](../../includes/hek-2-md.md)], viene visualizzato un messaggio. Il database deve essere riavviato per rendere effettivo l'annullamento dell'associazione.  
  
```sql  
sys.sp_xtp_unbind_db_resource_pool 'Hekaton_DB'  
```  
  
## <a name="requirements"></a>Requisiti  
  
-   Nel database specificato da `database_name` deve essere inclusa un'associazione a un pool di risorse di [!INCLUDE[hek_2](../../includes/hek-2-md.md)].  
  
-   È richiesta l'autorizzazione CONTROL SERVER.  
  
## <a name="see-also"></a>Vedere anche  
 [Associazione di un database con tabelle con ottimizzazione per la memoria a un pool di risorse](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [Sys.sp_xtp_bind_db_resource_pool & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql.md)  
  
  
