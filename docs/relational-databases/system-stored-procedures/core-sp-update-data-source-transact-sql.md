---
title: core.sp_update_data_source (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_update_data_source
- sp_update_data_source_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_data_source
- management data warehouse, data collector stored procedures
- core.sp_update_data_source stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 66b95f96-6df7-4657-9b3c-86a58c788ca5
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3156ef5a6d4d1af2298222b660e6483eb109cddd
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237959"
---
# <a name="corespupdatedatasource-transact-sql"></a>core.sp_update_data_source (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiorna una riga esistente o inserisce una nuova riga nella tabella core.source_info_internal del data warehouse di gestione. Questa routine viene chiamata dal componente di runtime dell'agente di raccolta dati tutte le volte che un pacchetto di caricamento avvia il caricamento dei dati nel data warehouse di gestione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
core.sp_update_data_source [ @collection_set_uid = ] 'collection_set_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @days_until_expiration = ] days_until_expiration  
    , [ @source_id = ] source_id OUTPUT  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @collection_set_uid =] '*collection_set_uid*'  
 GUID per il set di raccolta. *collection_set_uid* viene **uniqueidentifier**, senza alcun valore predefinito. Per ottenere il GUID, eseguire una query sulla vista dbo.syscollector_collection_sets nel database msdb.  
  
 [ @machine_name =] '*nome_computer*'  
 Nome del server in cui risiede l'insieme di raccolta. *nome_computer* viene **sysname** non prevede alcun valore predefinito.  
  
 [ @named_instance =] '*named_instance*'  
 Nome dell'istanza per l'insieme di raccolta. *named_instance* viene **sysname**, senza alcun valore predefinito.  
  
> [!NOTE]  
>  *named_instance* deve essere il nome, nome completo dell'istanza che include il nome del computer e il nome dell'istanza nel formato *nomecomputer*\\*instancename*.  
  
 [ @days_until_expiration =] *days_until_expiration*  
 Numero di giorni rimanenti del periodo di memorizzazione dei dati dello snapshot. *days_until_expiration* viene **smallint**.  
  
 [ @source_id =] *source_id*  
 Identificatore univoco per l'origine dell'aggiornamento. *Source_ID* viene **int** e viene restituito come OUTPUT.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Ogni volta che un pacchetto di caricamento inizia a caricare i dati nel data warehouse di gestione, il componente di runtime dell'agente di raccolta dati chiama core.sp_update_data_source. La tabella core.source_info_internal viene aggiornata se dopo l'ultimo caricamento si è verificata una delle modifiche seguenti:  
  
-   È stato aggiunto un nuovo set di raccolta.  
  
-   È stato modificato il valore di days_until_expiration.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **mdw_writer** (con autorizzazione EXECUTE) ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene aggiornata l'origine dati (in questo caso il set di raccolta Utilizzo disco), viene impostato il numero di giorni che mancano alla scadenza e viene restituito l'identificatore per l'origine. In questo esempio viene utilizzata l'istanza predefinita.  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @source_id int;  
EXEC core.sp_update_data_source   
@collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
@machine_name = '<computername>',  
@named_instance = 'MSSQLSERVER',  
@days_until_expiration = 10,  
@source_id = @source_id OUTPUT;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Data warehouse di gestione](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
