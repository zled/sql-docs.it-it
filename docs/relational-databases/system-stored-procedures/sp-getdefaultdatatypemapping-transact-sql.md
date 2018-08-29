---
title: sp_getdefaultdatatypemapping (Transact-SQL) | Microsoft Docs
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
- sp_getdefaultdatatypemapping_TSQL
- sp_getdefaultdatatypemapping
helpviewer_keywords:
- sp_getdefaultdatatypemapping
ms.assetid: b8401de1-f135-41d0-ba79-ce8fe1f48c00
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ff9df7e27545aa130398e0a81ffcf24855503aba
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025710"
---
# <a name="spgetdefaultdatatypemapping-transact-sql"></a>sp_getdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sul mapping predefinito per il tipo di dati specificato tra [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gestione sistema di database (DBMS). Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
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
  
|valore|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|L'origine è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|L'origine è un database Oracle.|  
  
 Questo parametro è obbligatorio.  
  
 [  **@source_version=** ] **'***source_version***'**  
 Numero di versione del DBMS di origine. *source_version* viene **varchar (10)**, con un valore predefinito NULL.  
  
 [ **@source_type**=] **'***source_type***'**  
 Tipo di dati nel sistema DBMS di origine. *source_type* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@source_length=** ] *source_length*  
 Lunghezza del tipo di dati nel DBMS di origine. *source_length* viene **bigint**, con un valore predefinito NULL.  
  
 [  **@source_precision=** ] *source_precision*  
 Precisione del tipo di dati nel DBMS di origine. *source_precision* viene **bigint**, con un valore predefinito NULL.  
  
 [  **@source_scale=** ] *source_scale*  
 Scala del tipo di dati nel DBMS di origine. *source_scale* viene **int**, con un valore predefinito NULL.  
  
 [  **@source_nullable=** ] *source_nullable*  
 Specifica se il tipo dati nel DBMS di origine ammette valori NULL. *source_nullable* viene **bit**, con valore predefinito è **1**, il che significa che i valori NULL sono supportati.  
  
 [ **@destination_dbms** =] **'***destination_dbms***'**  
 Nome del sistema DBMS di destinazione. *destination_dbms* viene **sysname**, e può essere uno dei valori seguenti:  
  
|valore|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|La destinazione è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|La destinazione è un database Oracle.|  
|**DB2**|La destinazione è un database IBM DB2.|  
|**SYBASE**|La destinazione è un database Sybase.|  
  
 Questo parametro è obbligatorio.  
  
 [ **@destination_version**=] **'***destination_version***'**  
 Numero di versione del DBMS di destinazione. *destination_version* viene **varchar (10)**, con un valore predefinito NULL.  
  
 [ **@destination_type**=] **'***destination_type***'** OUTPUT  
 Tipo di dati nel DBMS di destinazione. *destination_type* viene **sysname**, con un valore predefinito NULL.  
  
 [  **@destination_length=** ] *destination_length* OUTPUT  
 Lunghezza del tipo di dati nel DBMS di destinazione. *destination_length* viene **bigint**, con un valore predefinito NULL.  
  
 [  **@destination_precision=** ] *destination_precision* OUTPUT  
 Precisione del tipo di dati nel DBMS di destinazione. *destination_precision* viene **bigint**, con un valore predefinito NULL.  
  
 [  **@destination_scale=** ] *destination_scale * * * OUTPUT**  
 Scala del tipo di dati nel DBMS di destinazione. *destination_scale* viene **int**, con un valore predefinito NULL.  
  
 [  **@destination_nullable=** ] *destination_nullable * * * OUTPUT**  
 Specifica se il tipo di dati nel DBMS di destinazione ammette valori NULL. *destination_nullable* viene **bit**, con un valore predefinito NULL. **1** indica che i valori NULL sono supportati.  
  
 [  **@dataloss=** ] *perdita di dati * * * OUTPUT**  
 Specifica se il mapping può causare perdite di dati. *perdita di dati* viene **bit**, con un valore predefinito NULL. **1** significa che vi è un potenziale perdita di dati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_getdefaultdatatypemapping** viene utilizzata in tutti i tipi di replica tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBMS.  
  
 **sp_getdefaultdatatypemapping** restituisce i dati di destinazione predefinito tipo che rappresenta la corrispondenza più vicina per il tipo di dati di origine specificato.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_getdefaultdatatypemapping**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Sottoscrittori Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md)  
  
  
