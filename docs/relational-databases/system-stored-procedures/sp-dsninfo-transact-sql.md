---
title: sp_dsninfo (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/04/2017
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
- sp_dsninfo
- sp_dsninfo_TSQL
helpviewer_keywords:
- sp_dsninfo
ms.assetid: 34648615-814b-42bc-95a3-50e86b42ec4d
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aa1403655e8ad134f8d214cffcecf916c881bb40
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spdsninfo-transact-sql"></a>sp_dsninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sull'origine dati ODBC o OLE DB provenienti dal server di distribuzione associato al server corrente. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dsninfo [ @dsn =] 'dsn'   
    [ , [ @infotype =] 'info_type']   
    [ , [ @login =] 'login']   
    [ , [ @password =] 'password']  
    [ , [ @dso_type=] dso_type]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@dsn =**] **'***dsn***'**  
 Nome del server collegato DSN ODBC o OLE DB. *DSN* viene **varchar(128)**, non prevede alcun valore predefinito.  
  
 [  **@infotype =**] **'***Info***'**  
 Tipo di informazioni che si desidera ottenere. Se *Info* viene omesso o se si specifica NULL, vengono restituiti tutti i tipi di informazioni. *Info* viene **varchar(128)**, con un valore predefinito è NULL, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**DBMS_NAME**|Specifica il nome del produttore dell'origine dati.|  
|**DBMS_VERSION**|Specifica la versione dell'origine dati.|  
|**DATABASE_NAME**|Specifica il nome del database.|  
|**SQL_SUBSCRIBER**|Specifica che l'origine dati può essere un Sottoscrittore.|  
  
 [  **@login =**] **'***account di accesso***'**  
 Account di accesso per l'origine dati. Se l'origine dati include un account di accesso, specificare NULL oppure omettere il parametro. *account di accesso*viene **varchar(128)**, con un valore predefinito è NULL.  
  
 [  **@password =**] **'***password***'**  
 Password per l'account di accesso. Se l'origine dati include un account di accesso, specificare NULL oppure omettere il parametro. *password*viene **varchar(128)**, con un valore predefinito è NULL.  
  
 [  **@dso_type=**] *dso_type*  
 Tipo dell'origine dati. *dso_type* viene **int**, e può essere uno dei valori seguenti.  
  
|Value|Description|  
|-----------|-----------------|  
|**1** (impostazione predefinita)|Origine dati ODBC|  
|**3**|Origine dati OLE DB|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**Tipo di informazioni**|**nvarchar(64)**|Tipi di informazioni quali DBMS_NAME, DBMS_VERSION, DATABASE_NAME, SQL_SUBSCRIBER|  
|**Valore**|**nvarchar(512)**|Valore del tipo di informazioni associato.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_dsninfo** viene utilizzata in tutti i tipi di replica.  
  
 **sp_dsninfo** recupera informazioni origine dati ODBC o OLE DB che indica se il database può essere utilizzato per la replica o l'esecuzione di query.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_dsninfo**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_enumdsn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
