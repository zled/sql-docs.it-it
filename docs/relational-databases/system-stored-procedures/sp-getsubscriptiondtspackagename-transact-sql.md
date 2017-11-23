---
title: sp_getsubscriptiondtspackagename (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- sp_getsubscriptiondtspackagename
- sp_getsubscriptiondtspackagename_TSQL
helpviewer_keywords: sp_getsubscriptiondtspackagename
ms.assetid: 606c40aa-2593-43af-9762-0f260bbb51f2
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80eaff3653634de814935f31b9312ab5db17f0f4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="spgetsubscriptiondtspackagename-transact-sql"></a>sp_getsubscriptiondtspackagename (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il nome del pacchetto DTS (Data Transformation Services) utilizzato per trasformare i dati prima di inviarli a un Sottoscrittore. Questa stored procedure viene eseguita in qualsiasi database del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_getsubscriptiondtspackagename [ @publication = ] 'publication'   
    [ , [ @subscriber = ] 'subscriber' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication** =] **'***pubblicazione***'**  
 Nome della pubblicazione. **'***pubblicazione***'** è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@subscriber=**] **'***sottoscrittore***'**  
 Nome del Sottoscrittore. *Sottoscrittore* è di tipo sysname e il valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**new_package_name**|**sysname**|Nome del pacchetto DTS.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_getsubscriptiondtspackagename** viene utilizzata nella replica snapshot e transazionale.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_getsubscriptiondtspackagename**.  
  
  
