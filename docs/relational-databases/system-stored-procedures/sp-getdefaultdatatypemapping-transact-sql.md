---
title: sp_getdefaultdatatypemapping (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
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
- sp_getdefaultdatatypemapping_TSQL
- sp_getdefaultdatatypemapping
helpviewer_keywords:
- sp_getdefaultdatatypemapping
ms.assetid: b8401de1-f135-41d0-ba79-ce8fe1f48c00
caps.latest.revision: 18
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 398ed7c0cfb5123b649901b91ef95b7c7282ab6e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="spgetdefaultdatatypemapping-transact-sql"></a>sp_getdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sul mapping predefinito per il tipo di dati specificato tra [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database (DBMS) di sistema di gestione. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_getdefaultdatatypemapping [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
        , [ @source_type = ] 'source_type'    
    [ , [ @source_length = ] source_length ]  
    [ , [ @source_precision = ] source_precision ]  
    [ , [ @source_scale = ] source_scale ]  
    [ , [ @source_nullable = ] source_nullable ]  
        , [ @destination_dbms = ] 'destination_dbms'   
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' OUTPUT ]  
    [ , [ @destination_length = ] destination_length OUTPUT ]  
    [ , [ @destination_precision = ] destination_precision OUTPUT ]  
    [ , [ @destination_scale = ] destination_scale OUTPUT ]  
    [ , [ @destination_nullable = ] source_nullable OUTPUT ]  
    [ , [ @dataloss = ] dataloss OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@source_dbms**=] **'***source_dbms***'**  
 Nome del DBMS da cui viene eseguito il mapping dei tipi di dati. *source_dbms* viene **sysname**, e può essere uno dei valori seguenti:  
  
|Value|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|L'origine è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|L'origine è un database Oracle.|  
  
 Questo parametro è obbligatorio.  
  
 [  **@source_version=** ] **'***source_version***'**  
 Numero di versione del DBMS di origine. *source_version* viene **varchar(10**, con valore predefinito è NULL.  
  
 [ **@source_type**=] **'***source_type***'**  
 Tipo di dati nel sistema DBMS di origine. *source_type* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@source_length=** ] *source_length*  
 Lunghezza del tipo di dati nel DBMS di origine. *source_length* viene **bigint**, con valore predefinito è NULL.  
  
 [  **@source_precision=** ] *source_precision*  
 Precisione del tipo di dati nel DBMS di origine. *source_precision* viene **bigint**, con valore predefinito è NULL.  
  
 [  **@source_scale=** ] *source_scale*  
 Scala del tipo di dati nel DBMS di origine. *source_scale* viene **int**, con valore predefinito è NULL.  
  
 [  **@source_nullable=** ] *source_nullable*  
 Specifica se il tipo dati nel DBMS di origine ammette valori NULL. *source_nullable* viene **bit**, con valore predefinito è **1**, il che significa che i valori NULL sono supportati.  
  
 [ **@destination_dbms** =] **'***destination_dbms***'**  
 Nome del sistema DBMS di destinazione. *destination_dbms* viene **sysname**, e può essere uno dei valori seguenti:  
  
|Value|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|La destinazione è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|La destinazione è un database Oracle.|  
|**DB2**|La destinazione è un database IBM DB2.|  
|**SYBASE**|La destinazione è un database Sybase.|  
  
 Questo parametro è obbligatorio.  
  
 [ **@destination_version**=] **'***destination_version***'**  
 Numero di versione del DBMS di destinazione. *destination_version* viene **varchar(10**, con valore predefinito è NULL.  
  
 [ **@destination_type**=] **'***destination_type***'** OUTPUT  
 Tipo di dati nel DBMS di destinazione. *destination_type* viene **sysname**, con valore predefinito è NULL.  
  
 [  **@destination_length=** ] *destination_length* OUTPUT  
 Lunghezza del tipo di dati nel DBMS di destinazione. *destination_length* viene **bigint**, con valore predefinito è NULL.  
  
 [  **@destination_precision=** ] *destination_precision* OUTPUT  
 Precisione del tipo di dati nel DBMS di destinazione. *destination_precision* viene **bigint**, con valore predefinito è NULL.  
  
 [  **@destination_scale=** ] *destination_scale * * * OUTPUT**  
 Scala del tipo di dati nel DBMS di destinazione. *destination_scale* viene **int**, con valore predefinito è NULL.  
  
 [  **@destination_nullable=** ] *destination_nullable * * * OUTPUT**  
 Specifica se il tipo di dati nel DBMS di destinazione ammette valori NULL. *destination_nullable* viene **bit**, con valore predefinito è NULL. **1** indica che i valori NULL sono supportati.  
  
 [  **@dataloss=** ] *dataloss * * * OUTPUT**  
 Specifica se il mapping può causare perdite di dati. *DataLoss* viene **bit**, con valore predefinito è NULL. **1** significa che vi sia un potenziale perdita di dati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_getdefaultdatatypemapping** viene utilizzata in tutti i tipi di replica tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBMS.  
  
 **sp_getdefaultdatatypemapping** restituisce i dati di destinazione predefiniti tipo che rappresenta la corrispondenza più vicina al tipo di dati di origine specificato.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_getdefaultdatatypemapping**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Sottoscrittori Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md)  
  
  
