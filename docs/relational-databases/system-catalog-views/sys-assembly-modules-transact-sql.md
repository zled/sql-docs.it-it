---
title: Sys. assembly_modules (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.assembly_modules
- sys.assembly_modules_TSQL
- assembly_modules
- assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_modules catalog view
ms.assetid: 5f9e644e-8065-49a2-b53d-db7df98f70d8
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d457f00cdab5d8b7e6584c895c9a9070a1d9e395
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="sysassemblymodules-transact-sql"></a>sys.assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Restituisce una riga per ogni funzione, procedura o trigger definito da un assembly CLR (Common Language Runtime). Questa vista del catalogo esegue il mapping di stored procedure CLR, trigger CLR o funzioni CLR all'implementazione sottostante corrispondente. Gli oggetti di tipo TA, AF, PC, FS e FT sono associati a un modulo in assembly. Per trovare l'associazione tra oggetto e assembly, è possibile unire questa vista del catalogo ad altre viste. Ad esempio, quando si crea una stored procedure CLR, è rappresentato da una riga in **Sys. Objects**, una riga **Procedures** (che eredita da **Sys. Objects**), e una riga in **assembly_modules**. La stored procedure stessa è rappresentata dai metadati in **Sys. Objects** e **Procedures**. I riferimenti all'implementazione CLR sottostante della stored procedure vengono trovati **assembly_modules**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Numero di identificazione dell'oggetto SQL. Valore univoco all'interno di un database.|  
|**assembly_id**|**int**|ID dell'assembly da cui è stato creato questo modulo.|  
|**assembly_class**|**sysname**|Nome della classe nell'assembly che definisce il modulo corrente.|  
|**assembly_method**|**sysname**|Nome del metodo all'interno di **assembly_class** che definisce questo modulo.<br /><br /> Restituisce NULL per le funzioni di aggregazione (AF).|  
|**null_on_null_input**|**bit**|Il modulo è stato dichiarato in modo da produrre un output NULL per qualsiasi input NULL.|  
|**execute_as_principal_id**|**int**|ID dell'entità di database nella quale si verifica l'esecuzione del contesto nella modalità specificata dalla clausola EXECUTE AS della funzione CLR, della stored procedure CLR o del trigger CLR.<br /><br /> NULL = EXECUTE AS CALLER Impostazione predefinita.<br /><br /> ID dell'entità di database specificata = EXECUTE AS SELF, EXECUTE AS *nome_utente*, o EXECUTE AS *login_name*.<br /><br /> -2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
