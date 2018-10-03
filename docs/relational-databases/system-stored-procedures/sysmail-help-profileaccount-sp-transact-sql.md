---
title: sysmail_help_profileaccount_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_profileaccount_sp_TSQL
- sysmail_help_profileaccount_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_profileaccount_sp
ms.assetid: 3ea68271-0a6b-4d77-991c-4757f48f747a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 779519ef5ba3098e205a70d8c5923adc993f44f6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47700750"
---
# <a name="sysmailhelpprofileaccountsp-transact-sql"></a>sysmail_help_profileaccount_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elenca gli account associati a uno o più profili di Posta elettronica database.  
    
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_help_profileaccount_sp  
   {   [ @profile_id = ] profile_id   
      | [ @profile_name = ] 'profile_name' }  
   [ , {   [ @account_id = ] account_id  
         | [ @account_name = ] 'account_name' } ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@profile_id** = ] *profile_id*  
 ID del profilo che si desidera visualizzare nell'elenco. *profile_id* viene **int**, con un valore predefinito è NULL. Entrambi *profile_id* oppure *profile_name* deve essere specificato.  
  
 [ **@profile_name** =] **'***profile_name***'**  
 Nome del profilo che si desidera visualizzare nell'elenco. *profile_name* viene **sysname**, con un valore predefinito è NULL. Entrambi *profile_id* oppure *profile_name* deve essere specificato.  
  
 [ **@account_id** = ] *account_id*  
 ID dell'account che si desidera visualizzare nell'elenco. *account_id* viene **int**, con un valore predefinito è NULL. Quando *account_id* e *account_name* sono entrambi NULL, vengono elencati tutti gli account nel profilo.  
  
 [ **@account_name** =] **'***account_name***'**  
 Nome dell'account che si desidera visualizzare nell'elenco. *account_name* viene **sysname**, con un valore predefinito è NULL. Quando *account_id* e *account_name* sono entrambi NULL, vengono elencati tutti gli account nel profilo.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Viene restituito un set di risultati con le colonne seguenti.  
  
||||  
|-|-|-|  
|Nome colonna|Tipo di dati|Description|  
|**profile_id**|**int**|ID del profilo.|  
|**profile_name**|**sysname**|Nome del profilo.|  
|**account_id**|**int**|ID dell'account.|  
|**account_name**|**sysname**|Nome dell'account.|  
|**sequence_number**|**int**|Numero di sequenza dell'account all'interno del profilo.|  
  
## <a name="remarks"></a>Note  
 Se non si specifica *profile_id* oppure *profile_name* è specificato, questa stored procedure restituisce informazioni per tutti i profili nell'istanza.  
  
 La stored procedure **sysmail_help_profileaccount_sp** è nel **msdb** database ed è di proprietà di **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Le autorizzazioni per questa routine per impostazione predefinita ai membri di esecuzione per il **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 **A. Elenco di account per un profilo specifico in base al nome**  
  
 Nell'esempio seguente viene visualizzato un elenco di informazioni per il profilo `AdventureWorks Administrator` specificando il nome del profilo.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp  
   @profile_name = 'AdventureWorks Administrator';  
```  
  
 Quello che segue è un set di risultati di esempio, modificato per adattarlo alla lunghezza di riga.  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
```  
  
 **B. Elenco di account per un ID del profilo dal profilo specifico**  
  
 Nell'esempio seguente viene visualizzato un elenco di informazioni per il profilo `AdventureWorks Administrator` specificando l'ID del profilo.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp  
    @profile_id = 131 ;  
```  
  
 Quello che segue è un set di risultati di esempio, modificato per adattarlo alla lunghezza di riga.  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
```  
  
 **C. Elenco di account per tutti i profili**  
  
 Nell'esempio seguente viene visualizzato un elenco di account per tutti i profili nell'istanza.  
  
```  
EXECUTE msdb.dbo.sysmail_help_profileaccount_sp;  
```  
  
 Quello che segue è un set di risultati di esempio, modificato per adattarlo alla lunghezza di riga.  
  
```  
profile_id  profile_name                 account_id  account_name         sequence_number  
----------- ---------------------------- ----------- -------------------- ---------------  
131         AdventureWorks Administrator 197         Admin-MainServer     1  
131         AdventureWorks Administrator 198         Admin-BackupServer   2  
106         AdventureWorks Operator      210         Operator-MainServer  1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Creare un Account di posta elettronica Database](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Oggetti di configurazione di posta elettronica database](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Stored procedure di posta elettronica database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
