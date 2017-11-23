---
title: sp_generatefilters (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_generatefilters
- sp_generatefilters_TSQL
helpviewer_keywords: sp_generatefilters
ms.assetid: 0aeb5b7a-89d1-4bd5-a371-c27fa924360a
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b172784c5530264344d79e63702e50747a7de833
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spgeneratefilters-transact-sql"></a>sp_generatefilters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea filtri sulle tabelle della chiave esterna quando viene replicata una tabella specifica. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_generatefilters [ @publication =] 'publication'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione da filtrare. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_generatefilters** viene utilizzata nella replica di tipo merge.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_generatefilters**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_bindsession &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-bindsession-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
