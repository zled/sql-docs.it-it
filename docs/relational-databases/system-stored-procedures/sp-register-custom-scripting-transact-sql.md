---
title: sp_register_custom_scripting (Transact-SQL) | Documenti Microsoft
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
- sp_register_custom_scripting
- sp_register_custom_scripting_TSQL
helpviewer_keywords:
- sp_register_custom_scripting
ms.assetid: a8159282-de3b-4b9e-bdc9-3d3fce485c7f
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c2220495d256e1f38aecd5cd64c8d43a88c8f25f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spregistercustomscripting-transact-sql"></a>sp_register_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La replica consente di sostituire una o più stored procedure predefinite utilizzate per la replica transazionale con stored procedure personalizzate definite dall'utente. Quando viene apportata una modifica dello schema a una tabella replicata, queste stored procedure vengono ricreate. **sp_register_custom_scripting** registra una stored procedure o [!INCLUDE[tsql](../../includes/tsql-md.md)] file script che viene eseguito quando si verifica una modifica dello schema nello script la definizione per una nuovo utente-stored procedure personalizzata definita. Questa nuova stored procedure personalizzata definita dall'utente deve riflettere il nuovo schema della tabella. **sp_register_custom_scripting** viene eseguita nel database di pubblicazione, server di pubblicazione e la stored procedure o un file script registrato viene eseguita nel Sottoscrittore quando si verifica una modifica dello schema.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_register_custom_scripting [ @type  = ] 'type'  
    [ @value = ] 'value'   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@type** =] **'***tipo***'**  
 Tipo di stored procedure personalizzata o script da registrare. *tipo di* viene **varchar(16)** e non prevede alcun valore predefinito può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**insert**|La stored procedure personalizzata registrata viene eseguita quando viene replicata un'istruzione INSERT.|  
|**Aggiornamento**|La stored procedure personalizzata registrata viene eseguita quando viene replicata un'istruzione UPDATE.|  
|**delete**|La stored procedure personalizzata registrata viene eseguita quando viene replicata un'istruzione DELETE.|  
|**custom_script**|Lo script viene eseguito alla fine del trigger DDL (Data Definition Language).|  
  
 [ **@value**=] **'***valore***'**  
 Nome di una stored procedure o nome e percorso completo del file script [!INCLUDE[tsql](../../includes/tsql-md.md)] da registrare. *valore* viene **nvarchar(1024)**, non prevede alcun valore predefinito.  
  
> [!NOTE]  
>  Specificare NULL per *valore*parametro annullerà la registrazione di uno script registrato in precedenza, che corrisponde all'esecuzione [sp_unregister_custom_scripting](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md).  
  
 Quando il valore di *tipo* è **custom_script**, il nome e percorso completo di un [!INCLUDE[tsql](../../includes/tsql-md.md)] è previsto il file di script. In caso contrario, *valore* deve essere il nome di una stored procedure registrata.  
  
 [ **@publication**=] **'***pubblicazione***'**  
 Nome della pubblicazione per cui viene registrato lo script o la stored procedure personalizzata. *pubblicazione* viene **sysname**, il valore predefinito è **NULL**.  
  
 [ **@article**=] **'***articolo***'**  
 Nome dell'articolo per cui viene registrato lo script o la stored procedure personalizzata. *articolo* viene **sysname**, il valore predefinito è **NULL**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_register_custom_scripting** viene utilizzata nella replica snapshot e transazionale.  
  
 Questa stored procedure deve essere eseguita prima di apportare una modifica dello schema a una tabella replicata. Per ulteriori informazioni sull'utilizzo di questa stored procedure, vedere [procedure transazionali personalizzate di rigenerare per riflettere le modifiche dello Schema](../../relational-databases/replication/transactional/transactional-articles-regenerate-to-reflect-schema-changes.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database, o **db_ddladmin** ruolo predefinito del database possono eseguire **sp _ register_custom_scripting**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_unregister_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregister-custom-scripting-transact-sql.md)  
  
  
