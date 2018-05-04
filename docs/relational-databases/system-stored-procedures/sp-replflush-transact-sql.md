---
title: sp_replflush (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_replflush
- sp_replflush_TSQL
helpviewer_keywords:
- sp_replflush
ms.assetid: 20809f5f-941d-427f-8f0c-de7a6c487584
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e364f78b1bf69eba2ba120093607b71aa2080c2b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spreplflush-transact-sql"></a>sp_replflush (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Scarica la cache degli articoli. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
> [!IMPORTANT]  
>  Non dovrebbe risultare necessario eseguire questa procedura manualmente. **sp_replflush** deve essere utilizzato solo per la risoluzione dei problemi di replica come indicato da un professionista del supporto tecnico esperto della replica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replflush  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_replflush** viene utilizzata nella replica transazionale.  
  
 Le definizioni degli articoli vengono archiviate nella cache per migliorare il grado di efficienza. **sp_replflush** viene utilizzato da altre stored procedure di replica ogni volta che modifica o eliminazione della definizione di un articolo.  
  
 Una sola connessione client può disporre dell'accesso a un determinato database tramite un agente di lettura log. Se un client dispone di accesso di lettura log per un database, l'esecuzione **sp_replflush** fa sì che il client rilasciare l'accesso. Altri client può quindi analizzare il log delle transazioni tramite **sp_replcmds** o **sp_replshowcmds**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_replflush**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
