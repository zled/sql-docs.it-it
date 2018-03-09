---
title: sp_helpfilegroup (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ab59a2912f51882954420a81514b0fe2089f9a8f
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="sphelpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce i nomi e gli attributi dei filegroup associati al database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@filegroupname =** ] **'***nome***'**  
 Nome logico di un filegroup presente nel database corrente. *nome* è **sysname**, con un valore predefinito è NULL. Se *nome* viene omesso, vengono elencati tutti i filegroup nel database corrente e viene visualizzato solo il primo set di risultati illustrato nella sezione set di risultati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**GroupName**|**sysname**|Nome del filegroup|  
|**ID del gruppo**|**smallint**|Identificatore numerico del filegroup.|  
|**FileCount**|**int**|Numero di file del filegroup.|  
  
 Se *nome* è specificato, viene restituita una riga per ogni file nel filegroup.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|Nome logico del file nel filegroup.|  
|**fileid**|**smallint**|Identificatore numerico del file.|  
|**nome file**|**nchar(260)**|Nome fisico del file che include il percorso di directory.|  
|**size**|**nvarchar (15)**|Dimensione del file in kilobyte.|  
|**MaxSize**|**nvarchar (15)**|Dimensione massima del file.<br /><br /> Valore massimo fino a cui possono aumentare le dimensioni del file. Se questo campo include il valore UNLIMITED, le dimensioni del file possono aumentare fino a riempire il disco.|  
|**aumento delle dimensioni**|**nvarchar (15)**|Incremento per l'aumento delle dimensioni del file. Indica la quantità di spazio aggiunta al file ogni volta che è necessario spazio aggiuntivo.<br /><br /> 0 = la dimensione del file è fissa e non aumenterà.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>A. Restituzione di tutti i filegroup in un database  
 Nell'esempio seguente vengono restituite le informazioni sui filegroup nel database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>B. Restituzione di tutti i file in un filegroup  
 Nell'esempio seguente vengono restituite le informazioni relative a tutti i file nel filegroup `PRIMARY` nel database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [Sys. master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Sys. FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Filegroup e file di database](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  
