---
title: Assemblies (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.assemblies
- assemblies_TSQL
- sys.assemblies_TSQL
- assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assemblies catalog view
ms.assetid: e321753f-293f-42ab-b225-d118713df40b
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 22a200cee9b07332440076feb0981c1610682089
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38000873"
---
# <a name="sysassemblies-transact-sql"></a>sys.assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Restituisce una riga per ogni assembly.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome dell'assembly. Valore univoco all'interno del database.|  
|**principal_id**|**int**|ID dell'entità proprietaria dell'assembly.|  
|**assembly_id**|**int**|Numero di identificazione dell'assembly. Valore univoco all'interno di un database.|  
|**clr_name**|**nvarchar(4000)**|Stringa canonica che codifica il nome semplice, il numero di versione, le impostazioni internazionali, la chiave pubblica e l'architettura dell'assembly. Questo valore identifica in modo univoco l'assembly sul lato CLR (Common Language Runtime).|  
|**permission_set**|**tinyint**|Set di autorizzazioni o livello di sicurezza dell'assembly.<br /><br /> 1 = Accesso sicuro<br /><br /> 2 = Accesso esterno<br /><br /> 3 = Accesso non sicuro|  
|**permission_set_desc**|**nvarchar(60)**|Descrizione del set di autorizzazioni o del livello di sicurezza dell'assembly.<br /><br /> SAFE_ACCESS<br /><br /> EXTERNAL_ACCESS<br /><br /> UNSAFE_ACCESS|  
|**is_visible**|**bit**|1 = L'assembly è visibile per la registrazione di punti di ingresso [!INCLUDE[tsql](../../includes/tsql-md.md)].<br /><br /> 0 = L'assembly è destinato unicamente a chiamanti gestiti, ovvero fornisce un'implementazione interna per altri assembly del database.|  
|**create_date**|**datetime**|Data di creazione o registrazione dell'assembly.|  
|**modify_date**|**datetime**|Data di modifica dell'assembly.|  
|**is_user_defined**|**bit**|Indica l'origine dell'assembly.<br /><br /> 0 = assembly definiti dal sistema (ad esempio Types per il **hierarchyid** tipo di dati)<br /><br /> 1 = Assembly definiti dall'utente|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo di Assembly CLR &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ASSEMBLYPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/assemblyproperty-transact-sql.md)  
  
  
