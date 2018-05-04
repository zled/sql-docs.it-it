---
title: sp_adjustpublisheridentityrange (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
- sp_adjustpublisheridentityrange_TSQL
- sp_adjustpublisheridentityrange
helpviewer_keywords:
- sp_adjustpublisheridentityrange
ms.assetid: 64f111fd-fb7d-4459-93f7-65f0f8dd7efe
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: e8d39485c2ed9519353a2175fa4e127a5900b0e0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spadjustpublisheridentityrange-transact-sql"></a>sp_adjustpublisheridentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Regola l'intervallo di valori Identity in una pubblicazione e riassegna nuovi intervalli in base al valore soglia previsto per la pubblicazione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_adjustpublisheridentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @table_name = ] 'table_name' ]  
    [ , [ @table_owner= ] 'table_owner' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=**] **'***pubblicazione***'**  
 Nome della pubblicazione in cui vengono riallocati i nuovi intervalli di valori Identity. *pubblicazione* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@table_name=**] **'***table_name***'**  
 Nome della tabella in cui vengono riallocati i nuovi intervalli di valori Identity. *TABLE_NAME* viene **sysname**, con un valore predefinito è NULL.  
  
 [ **@table_owner=**] **'***table_owner***'**  
 Proprietario della tabella nel server di pubblicazione. *TABLE_OWNER* viene **sysname**, con un valore predefinito è NULL. Se *table_owner* viene omesso, viene utilizzato il nome dell'utente corrente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_adjustpublisheridentityrange** viene utilizzata in tutti i tipi di replica.  
  
 Nel caso di una pubblicazione per la quale è attivata la gestione automatica di intervalli di valori Identity, l'agente di distribuzione o di merge è responsabile della regolazione automatica dell'intervallo di valori Identity in una pubblicazione in base al valore soglia corrispondente. Tuttavia, se per qualche motivo l'agente di distribuzione o l'agente di Merge non è stato eseguito per un periodo di tempo e la risorsa dell'intervallo identità è stata utilizzata fino al punto di soglia, gli utenti possono chiamare **sp_adjustpublisheridentityrange** per allocare un nuovo intervallo di valori per un server di pubblicazione.  
  
 Quando si esegue **sp_adjustpublisheridentityrange**, *pubblicazione* o *table_name* deve essere specificato. Se vengono specificati entrambi oppure viene omesso uno dei due, viene restituito un errore.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_adjustpublisheridentityrange**.  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di colonne Identity](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
