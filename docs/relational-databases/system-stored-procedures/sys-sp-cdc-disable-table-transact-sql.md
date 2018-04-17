---
title: sp_cdc_disable_table (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_disable_table
- sp_cdc_disable_table
- sys.sp_cdc_disable_table_TSQL
- sp_cdc_disable_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_disable_table
- sys.sp_cdc_disable_table
- change data capture [SQL Server], disabling tables
ms.assetid: da2156c0-504e-4d76-b9a0-4448becf9bda
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d4364f6cba3a5eb28cfac72e4f5f727ddf1bd1ef
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sysspcdcdisabletable-transact-sql"></a>sys.sp_cdc_disable_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Disabilita Change Data Capture per la tabella di origine e l'istanza di acquisizione specificate nel database corrente. Change Data Capture non è disponibile in tutte le edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.sp_cdc_disable_table   
  [ @source_schema = ] 'source_schema' ,   
  [ @source_name = ] 'source_name'  
  [ , [ @capture_instance = ] 'capture_instance' | 'all' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@source_schema=** ] **'***source_schema***'**  
 Nome dello schema in cui è contenuta la tabella di origine. *source_schema* viene **sysname**, non prevede alcun valore predefinito e non può essere NULL.  
  
 *source_schema* deve esistere nel database corrente.  
  
 [  **@source_name=** ] **'***source_name***'**  
 Nome della tabella di origine da disabilitare la funzionalità di Change Data Capture. *source_name* viene **sysname**, non prevede alcun valore predefinito e non può essere NULL.  
  
 *source_name* deve esistere nel database corrente.  
  
 [  **@capture_instance=** ] **'***capture_instance***'** | **'**tutti**'**  
 Nome dell'istanza di acquisizione da disabilitare per la tabella di origine specificata. *capture_instance* viene **sysname** e non può essere NULL.  
  
 Se si specifica "all", tutte le istanze definite per di acquisizione *source_name* sono disabilitati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **Sys. sp_cdc_disable_table** cadute change data capture Modifica tabella e funzioni di sistema associate con l'istanza di acquisizione e tabella di origine specificata. Elimina tutte le righe associate a questa istanza di acquisizione specificata dal set di tabelle di sistema di change data capture di **is_tracked_by_cdc** colonna per la voce della tabella nel [Sys. Tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) vista del catalogo impostato su 0.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **db_owner** ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene disabilitata l'acquisizione dei dati delle modifiche per la tabella `HumanResources.Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_disable_table   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee',  
    @capture_instance = N'HumanResources_Employee';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys. sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)  
  
  
