---
title: sp_helpdb (Transact-SQL) | Documenti Microsoft
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
- sp_helpdb
- sp_helpdb_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpdb
ms.assetid: 4c3e3302-6cf1-4b2b-8682-004049b578c3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c1af0b93536006ba5f7b106c10935b07263a572b
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="sphelpdb-transact-sql"></a>sp_helpdb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni su un database specifico o su tutti i database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdb [ [ @dbname= ] 'name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@dbname=** ] **'***nome***'**  
 Nome del database per il quale vengono restituite informazioni. *nome* è **sysname**, non prevede alcun valore predefinito. Se *nome* non viene specificato, **sp_helpdb** segnala tutti i database di **Sys. Databases** vista del catalogo.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del database.|  
|**db_size**|**nvarchar(13)**|Dimensioni totali del database.|  
|**proprietario**|**sysname**|Proprietario del database, ad esempio **sa**.|  
|**DBID**|**smallint**|ID del database.|  
|**creato**|**nvarchar(11)**|Data di creazione del database.|  
|**status**|**nvarchar(600)**|Elenco separato da virgola dei valori delle opzioni impostate nel database.<br /><br /> Le opzioni con valori booleani vengono elencate solo se sono abilitate. Opzioni non booleane sono elencate con i relativi valori sotto forma di *option_name*=*valore*.<br /><br /> Per altre informazioni, vedere [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md).|  
|**COMPATIBILITY_LEVEL**|**tinyint**|Livello di compatibilità del database (60, 65, 70, 80 o 90).|  
  
 Se *nome* è specificato, è presente un set di risultati aggiuntivo che mostra l'allocazione di file per il database specificato.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nchar(128)**|Nome logico del file.|  
|**fileid**|**smallint**|ID di file.|  
|**nome file**|**nchar(260)**|Nome del file del sistema operativo, ovvero nome fisico del file.|  
|**filegroup**|**nvarchar(128)**|Filegroup a cui appartiene il file.<br /><br /> NULL = Il file è un file di log. Questo tipo di file non viene mai incluso in un filegroup.|  
|**size**|**nvarchar(18)**|Dimensione del file espressa in megabyte.|  
|**MaxSize**|**nvarchar(18)**|Dimensioni massime consentite per il file. Se questo campo include il valore UNLIMITED, le dimensioni del file possono aumentare fino a riempire il disco.|  
|**aumento delle dimensioni**|**nvarchar(18)**|Incremento per l'aumento delle dimensioni del file. Indica la quantità di spazio aggiunta al file ogni volta che è necessario spazio aggiuntivo.|  
|**utilizzo**|**varchar(9)**|Utilizzo del file. Per un file di dati, il valore è **'solo dati'** e per il file di log è il valore **'log solo'**.|  
  
## <a name="remarks"></a>Osservazioni  
 Il **stato** colonna nel risultato imposta le opzioni sono state impostate su ON nel database di report. Tutte le opzioni di database non vengono segnalate i **stato** colonna. Per visualizzare un elenco completo delle impostazioni del database, utilizzare il **Sys. Databases** vista del catalogo.  
  
## <a name="permissions"></a>Autorizzazioni  
 Quando viene specificato un singolo database, l'appartenenza al **pubblica** è necessario il ruolo del database. Quando è specificato alcun database, l'appartenenza al **pubblica** ruolo nel **master** database è obbligatorio.  
  
 Se non è possibile accedere a un database, **sp_helpdb** Visualizza messaggio 15622 e tutte le informazioni sugli errori del database, come avviene.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-returning-information-about-a-single-database"></a>A. Restituzione di informazioni su un solo database  
 Nell'esempio seguente vengono visualizzate informazioni sul database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
EXEC sp_helpdb N'AdventureWorks2012';  
```  
  
### <a name="b-returning-information-about-all-databases"></a>B. Restituzione di informazioni su tutti i database  
 Nell'esempio seguente vengono visualizzate informazioni su tutti i database nel server che esegue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
EXEC sp_helpdb;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [Sys. FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Sys. master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
