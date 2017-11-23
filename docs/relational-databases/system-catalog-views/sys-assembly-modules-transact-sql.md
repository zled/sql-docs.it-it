---
title: Sys. assembly_modules (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.assembly_modules
- sys.assembly_modules_TSQL
- assembly_modules
- assembly_modules_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.assembly_modules catalog view
ms.assetid: 5f9e644e-8065-49a2-b53d-db7df98f70d8
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 26866a8c8977b4fd707230d59b617b4594725d32
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
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
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
