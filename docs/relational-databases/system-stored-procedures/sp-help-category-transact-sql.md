---
title: sp_help_category (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_category
- sp_help_category_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_category
ms.assetid: 8cad1dcc-b43e-43bd-bea0-cb0055c84169
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 05e5ef298e9365b63b4e66b93c0f2aa637be8312
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706999"
---
# <a name="sphelpcategory-transact-sql"></a>sp_help_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sulle classi di processi, avvisi o operatori specificate.  
   
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_category [ [ @class = ] 'class' ]   
     [ , [ @type = ] 'type' ]   
     [ , [ @name = ] 'name' ]   
     [ , [ @suffix = ] suffix ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@class=**] **'***classe***'**  
 Classe su cui si desidera ottenere informazioni. *classe* viene **varchar (8)**, con valore predefinito è **processo**. *classe* può essere uno dei valori seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|**JOB**|Restituisce informazioni su una categoria di processi.|  
|**AVVISO**|Restituisce informazioni su una categoria di avvisi.|  
|**OPERATORE**|Restituisce informazioni su una categoria di operatori.|  
  
 [  **@type=** ] **'***tipo***'**  
 Tipo di categoria su cui vengono richieste informazioni. *tipo di* viene **varchar(12)**, con un valore predefinito è NULL, i possibili valori sono i seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|**LOCAL**|Categoria di processi locali.|  
|**MULTI-SERVER**|Categoria di processi multiserver.|  
|**NONE**|Categoria per una classe diversa da **processo**.|  
  
 [ **@name=** ] **'***name***'**  
 Nome della categoria su cui vengono richieste informazioni. *nome* viene **sysname**, con un valore predefinito è NULL.  
  
 [ **@suffix=** ] *suffix*  
 Specifica se il **category_type** colonna nel set di risultati è un ID o un nome. *suffisso* viene **bit**, il valore predefinito è **0**. **1** Mostra il **category_type** come nome, e **0** lo visualizza come ID.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Quando **@suffix** viene **0**, **sp_help_category** restituisce il set di risultati seguente:  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|ID della categoria|  
|**category_type**|**tinyint**|Tipo di categoria:<br /><br /> **1** = locale<br /><br /> **2** = multiserver<br /><br /> **3** = nessuno|  
|**name**|**sysname**|Nome della categoria|  
  
 Quando **@suffix** viene **1**, **sp_help_category** restituisce il set di risultati seguente:  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**category_id**|**int**|ID della categoria|  
|**category_type**|**sysname**|Tipo di categoria: Uno dei **locale**, **MULTISERVER**, o **NONE**|  
|**name**|**sysname**|Nome della categoria|  
  
## <a name="remarks"></a>Note  
 **sp_help_category** deve essere eseguita la **msdb** database.  
  
 Se non viene specificato alcun parametro, il set di risultati include informazioni su tutte le categorie dei processi.  
  
## <a name="permissions"></a>Permissions  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-local-job-information"></a>A. Restituzione di informazioni sui processi locali  
 Nell'esempio seguente vengono restituite informazioni sui processi gestiti a livello locale.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @type = N'LOCAL' ;  
GO  
```  
  
### <a name="b-returning-alert-information"></a>B. Restituzione di informazioni sugli avvisi  
 Nell'esempio seguente vengono restituite informazioni sulla categoria di avvisi Replication.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_category  
    @class = N'ALERT',  
    @name = N'Replication' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_delete_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-category-transact-sql.md)   
 [sp_update_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
