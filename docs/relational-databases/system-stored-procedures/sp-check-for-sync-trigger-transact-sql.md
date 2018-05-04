---
title: sp_check_for_sync_trigger (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
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
- filter_TSQL
- sp_check_for_sync_trigger
helpviewer_keywords:
- sp_check_for_sync_trigger
ms.assetid: 54a1e2fd-c40a-43d4-ac64-baed28ae4637
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a77f5bfd92ca2af52e6d8949a98e4aa24c908534
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spcheckforsynctrigger-transact-sql"></a>sp_check_for_sync_trigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Determina se una stored procedure definita dall'utente o un trigger definito dall'utente viene chiamato nel contesto di un trigger di replica utilizzato per sottoscrizioni ad aggiornamento immediato. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione o nel database di sottoscrizione del Sottoscrittore.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_check_for_sync_trigger [ @tabid = ] 'tabid'   
    [ , [ @trigger_op = ] 'trigger_output_parameters' OUTPUT ]  
    [ , [ @fonpublisher = ] fonpublisher ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@tabid =** ] '*tabid*'  
 ID di oggetto della tabella in cui vengono controllati i trigger per l'aggiornamento immediato. *tabid* viene **int** non prevede alcun valore predefinito.  
  
 [ **@trigger_op =** ] '*output_parameters*' OUTPUT  
 Specifica se il parametro di output restituisce il tipo di trigger da cui viene richiamato. *output_parameters* viene **char (10)** e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**Componenti aggiuntivi**|Trigger INSERT|  
|**UPD**|Trigger UPDATE|  
|**CANC**|Trigger DELETE|  
|NULL (predefinito)||  
  
 [  **@fonpublisher =** ] *fonpublisher*  
 Specifica la posizione in cui viene eseguita la stored procedure. *fonpublisher* viene **bit**, con valore predefinito è 0. 0 indica che l'esecuzione avviene nel Sottoscrittore, mentre 1 indica che avviene nel server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 indica che la stored procedure non viene richiamata nel contesto di un trigger per l'aggiornamento immediato. 1 indica che viene chiamato all'interno del contesto di un trigger di aggiornamento immediato ed è il tipo di trigger restituito in *@trigger_op*.  
  
## <a name="remarks"></a>Osservazioni  
 **sp_check_for_sync_trigger** viene utilizzata nella replica snapshot e transazionale.  
  
 **sp_check_for_sync_trigger** viene utilizzato per il coordinamento tra la replica e trigger definiti dall'utente. Questa stored procedure determina se viene richiamata nel contesto di un trigger di replica. Ad esempio, è possibile chiamare la routine **sp_check_for_sync_trigger** nel corpo di un trigger definito dall'utente. Se **sp_check_for_sync_trigger** restituisce **0**, il trigger definito dall'utente continua l'elaborazione. Se **sp_check_for_sync_trigger** restituisce **1**, il trigger definito dall'utente viene chiusa. Ciò garantisce che il trigger definito dall'utente non venga attivato quando il trigger di replica aggiorna la tabella.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il codice che può essere utilizzato in un trigger in una tabella del Sottoscrittore.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int  
SELECT @table_id = object_id('tablename')  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT  
IF @retcode = 1  
RETURN  
```  
  
## <a name="example"></a>Esempio  
 Inoltre è possibile aggiungere il codice a un trigger in una tabella nel server di pubblicazione; il codice è simile, ma la chiamata a **sp_check_for_sync_trigger** include un parametro aggiuntivo.  
  
```  
DECLARE @retcode int, @trigger_op char(10), @table_id int, @fonpublisher int  
SELECT @table_id = object_id('tablename')  
SELECT @fonpublisher = 1  
EXEC @retcode = sp_check_for_sync_trigger @table_id, @trigger_op OUTPUT, @fonpublisher  
IF @retcode = 1  
RETURN  
```  
  
## <a name="permissions"></a>Autorizzazioni  
 **sp_check_for_sync_trigger** stored procedure può essere eseguita da qualsiasi utente con autorizzazioni SELECT per il [Sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) vista di sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
