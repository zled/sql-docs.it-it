---
title: Sys. sp_cdc_disable_table (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b797301b5b778bea34ad1552152e7e3e147dde37
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169171"
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
 [  **@source_schema=** ] **'**_origine\_schema_**'**  
 Nome dello schema in cui è contenuta la tabella di origine. *source_schema* viene **sysname**, non prevede alcun valore predefinito e non può essere NULL.  
  
 *source_schema* deve esistere nel database corrente.  
  
 [  **@source_name=** ] **'**_origine\_nome_**'**  
 Nome della tabella di origine da disabilitare la funzionalità di Change Data Capture. *source_name* viene **sysname**, non prevede alcun valore predefinito e non può essere NULL.  
  
 *source_name* deve esistere nel database corrente.  
  
 [  **@capture_instance=** ] **'**_acquisire\_istanza_**'** | **'** tutti i **'**  
 Nome dell'istanza di acquisizione da disabilitare per la tabella di origine specificata. *capture_instance* viene **sysname** e non può essere NULL.  
  
 Quando si specifica "all", tutte le istanze di acquisizione definite per *source_name* sono disabilitati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="remarks"></a>Note  
 **Sys. sp_cdc_disable_table** cadute change data capture modificare tabelle e funzioni di sistema associate all'istanza di origine specificato nella tabella e lo stato capture. Elimina tutte le righe associate a questa istanza di acquisizione specificata dalla tabelle di sistema di change data capture e viene impostata la **is_tracked_by_cdc** colonna per la voce della tabella nel [Sys. Tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) vista del catalogo impostato su 0.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'appartenenza al **db_owner** ruolo predefinito del database.  
  
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
  
  
