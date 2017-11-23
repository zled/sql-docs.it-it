---
title: sp_linkedservers (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_linkedservers
- sp_linkedservers_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_linkedservers
ms.assetid: d8f82f78-8a1f-4831-bcee-7c36c6e7dfbb
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4f3dfaa1fca80d022529b1243ef1be0fe3415a68
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="splinkedservers-transact-sql"></a>sp_linkedservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce l'elenco dei server collegati definiti nel server locale.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_linkedservers  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o un numero diverso da zero (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**SRV_NAME**|**sysname**|Nome del server collegato.|  
|**SRV_PROVIDERNAME**|**nvarchar (**128**)**|Nome descrittivo del provider OLE DB che gestisce l'accesso al server collegato specificato.|  
|**SRV_PRODUCT**|**nvarchar (**128**)**|Nome del prodotto del server collegato.|  
|**SRV_DATASOURCE**|**nvarchar (**4000**)**|Proprietà dell'origine dei dati OLE DB corrispondente al server collegato specificato.|  
|**SRV_PROVIDERSTRING**|**nvarchar (**4000**)**|Proprietà della stringa del provider OLE DB corrispondente al server collegato.|  
|**SRV_LOCATION**|**nvarchar (**4000**)**|Proprietà della posizione OLE DB corrispondente al server collegato specificato.|  
|**SRV_CAT NON**|**sysname**|Proprietà del catalogo OLE DB corrispondente al server collegato specificato.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione SELECT per lo schema.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_columns_ex &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_foreignkeys &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_primarykeys &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_table_privileges &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [sp_tables_ex &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Query distribuite Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)  
  
  
