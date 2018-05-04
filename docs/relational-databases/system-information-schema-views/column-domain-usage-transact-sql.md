---
title: COLUMN_DOMAIN_USAGE (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-information-schema-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COLUMN_DOMAIN_USAGE_TSQL
- COLUMN_DOMAIN_USAGE
dev_langs:
- TSQL
helpviewer_keywords:
- INFORMATION_SCHEMA.COLUMN_DOMAIN_USAGE view
- COLUMN_DOMAIN_USAGE view
ms.assetid: deb20037-6a51-47ae-9f49-7601698fafaf
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c6980d71bf921065c0d460fcc9107a8d525dcd60
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="columndomainusage-transact-sql"></a>COLUMN_DOMAIN_USAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni colonna nel database corrente con un tipo di dati alias. Questa vista degli schemi delle informazioni restituisce informazioni sugli oggetti per i quali l'utente dispone di autorizzazioni.  
  
 Per recuperare informazioni da queste viste, specificare il nome completo di **INFORMATION_SCHEMA. * * * view_name*.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**DOMAIN_CATALOG**|**nvarchar (** 128 **)**|Database in cui è incluso il tipo di dati alias.|  
|**DOMAIN_SCHEMA**|**nvarchar (** 128 **)**|Nome dello schema che include il tipo di dati alias.<br /><br /> **\*\* Importante \* \***  non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un tipo di dati. L'unica modalità affidabile per cercare lo schema di un tipo consiste nell'utilizzare la funzione TYPEPROPERTY.|  
|**NOME_DOMINIO**|**sysname**|Tipo di dati alias.|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Qualificatore della tabella.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Proprietario della tabella.<br /><br /> **\*\* Importante \* \***  non utilizzare viste INFORMATION_SCHEMA per determinare lo schema di un oggetto. L'unica modalità affidabile per cercare lo schema di un oggetto consiste nell'eseguire una query sulla vista del catalogo sys.objects.|  
|**TABLE_NAME**|**sysname**|Tabella in cui viene utilizzato il tipo di dati alias.|  
|**COLUMN_NAME**|**sysname**|Colonna in cui viene utilizzato il tipo di dati alias.|  
  
## <a name="see-also"></a>Vedere anche  
 [Viste di sistema &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Viste degli schemi delle informazioni &#40;Transact-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  
