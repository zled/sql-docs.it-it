---
title: sp_helpdatatypemap (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sp_helpdatatypemap
- sp_helpdatatypemap_TSQL
helpviewer_keywords: sp_helpdatatypemap
ms.assetid: 800c9c65-723e-4961-a63d-327987f129f0
caps.latest.revision: "31"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d22a2c19f5824ef0a1cb5e0a145afd72492289df
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpdatatypemap-transact-sql"></a>sp_helpdatatypemap (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sui mapping dei tipi di dati definito tra [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database (DBMS) di sistemi di gestione. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdatatypemap [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @defaults_only = ] defaults_only ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@source_dbms** =] **'***source_dbms***'**  
 Nome del DBMS da cui viene eseguito il mapping dei tipi di dati. *source_dbms* è **sysname**, e può essere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|L'origine è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|L'origine è un database Oracle.|  
  
 [  **@source_version** =] **'***source_version***'**  
 Versione del prodotto del sistema DBMS di origine. *source_version*è **varchar (10)**, e se non specificato, il tipo di dati i mapping per tutte le versioni di origine vengono restituiti DBMS. Consente al set dei risultati di venire filtrato in base alla versione di origine del sistema DBMS.  
  
 [  **@source_type** =] **'***source_type***'**  
 Tipo di dati elencato nel sistema DBMS di origine. *source_type* è **sysname**, se non specificato, vengono restituiti i mapping per tutti i tipi di dati nel DBMS di origine. Consente al set di risultati di venire filtrato in base al tipo di dati nel sistema DBMS di origine.  
  
 [  **@destination_dbms**  =] **'***destination_dbms***'**  
 Nome del sistema DBMS di destinazione. *destination_dbms* è **sysname**, e può essere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|La destinazione è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|La destinazione è un database Oracle.|  
|**DB2**|La destinazione è un database IBM DB2.|  
|**SYBASE**|La destinazione è un database Sybase.|  
  
 [  **@destination_version** =] **'***destination_version***'**  
 Numero di versione del DBMS di destinazione. *destination_version*è **varchar (10)**, se non specificato, vengono restituiti i mapping per tutte le versioni del sistema DBMS di destinazione. Consente al set dei risultati di venire filtrato in base alla versione di destinazione del sistema DBMS.  
  
 [  **@destination_type** =] **'***destination_type***'**  
 Tipo di dati nel DBMS di destinazione. *destination_type*è **sysname**, se non specificato, vengono restituiti i mapping per tutti i tipi di dati nel DBMS di destinazione. Consente al set di risultati di venire filtrato in base al tipo di dati nel sistema DBMS di destinazione.  
  
 [  **@defaults_only** =] *defaults_only*  
 Vengono restituiti solo i mapping dei tipi di dati predefiniti. *defaults_only* è **bit**, il valore predefinito è **0**. **1** indica che solo i dati predefiniti i mapping dei tipi vengono restituiti. **0** indica che il valore predefinito e tutti i dati definiti dall'utente i mapping dei tipi vengono restituiti.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Description|  
|-----------------|-----------------|  
|**mapping_id**|Identifica il mapping dei tipi di dati.|  
|**source_dbms**|Nome e numero di versione del sistema DBMS di origine.|  
|**source_type**|Tipo di dati nel sistema DBMS di origine.|  
|**destination_dbms**|Nome del sistema DBMS di destinazione.|  
|**destination_type**|Tipo di dati nel sistema DBMS di destinazione.|  
|**is_default**|Indica il mapping predefinito o un mapping alternativo. Il valore **0** indica che il mapping è definito dall'utente.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helpdatatypemap** definisce i mapping dei tipi di dati dal Server di pubblicazione non SQL e da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] server di pubblicazione non[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i sottoscrittori.  
  
 Quando la combinazione specificata di origine e di DBMS di destinazione non è supportata, **sp_helpdatatypemap** restituisce un set di risultati vuoto.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** al server di distribuzione o i membri del ruolo predefinito del server di **db_owner** ruolo predefinito del database nel database di distribuzione possono eseguire **sp_helpdatatypemap**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_getdefaultdatatypemapping &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)  
  
  
