---
title: TABLE_PRIVILEGES (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-information-schema-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TABLE_PRIVILEGES_TSQL
- TABLE_PRIVILEGES
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.TABLE_PRIVILEGES view
- TABLE_PRIVILEGES view
ms.assetid: 70269d26-b085-4a98-8a9f-b4742c2848bd
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d710b2318a52d307facd37bbd6b03a8c22e54d69
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="tableprivileges-transact-sql"></a>TABLE_PRIVILEGES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni privilegio di tabella concesso a o dall'utente corrente nel database in uso.  
  
 Per recuperare informazioni da queste viste, specificare il nome completo di **INFORMATION_SCHEMA.** *view_name*.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**GRANTOR**|**nvarchar (**128**)**|Utente che concede il privilegio.|  
|**UTENTE AUTORIZZATO**|**nvarchar (**128**)**|Beneficiario del privilegio.|  
|**TABLE_CATALOG**|**nvarchar (**128**)**|Qualificatore della tabella.|  
|**TABLE_SCHEMA**|**nvarchar (**128**)**|Nome dello schema che contiene la tabella.<br /><br /> **\*\*Importante \* \***  non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un oggetto. L'unica modalità affidabile per cercare lo schema di un oggetto consiste nell'eseguire una query sulla vista del catalogo sys.objects.|  
|**TABLE_NAME**|**sysname**|Nome della tabella.|  
|**PRIVILEGE_TYPE**|**varchar (**10**)**|Tipo di privilegio.|  
|**IS_GRANTABLE**|**varchar (**3**)**|Specifica se il beneficiario può concedere autorizzazioni ad altri utenti.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40; Transact-SQL &#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Viste degli schemi delle informazioni &#40; Transact-SQL &#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [Sys. Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [Sys. database_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [Sys. server_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)  
  
  
