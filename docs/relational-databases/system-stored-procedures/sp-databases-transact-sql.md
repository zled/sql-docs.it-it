---
title: sp_databases (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_databases_TSQL
- sp_databases
dev_langs:
- TSQL
helpviewer_keywords:
- sp_databases
ms.assetid: 2a83b92a-9ecc-43c4-8ff4-e91e3a940b5a
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c22415c34f0e25dc1117b6a5f86839c66f0ba53b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "33238002"
---
# <a name="spdatabases-transact-sql"></a>sp_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elenca i database disponibili in un'istanza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o accessibili tramite un gateway di database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_databases  
```  
  
## <a name="return-code-values"></a>Valori restituiti  
 None  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**DATABASE_NAME**|**sysname**|Nome del database. Nel [!INCLUDE[ssDE](../../includes/ssde-md.md)], questa colonna rappresenta il nome del database archiviata nel **Sys. Databases** vista del catalogo.|  
|**DATABASE_SIZE**|**int**|Dimensioni del database in kilobyte.|  
|**SEZIONE OSSERVAZIONI**|**varchar(254)**|In [!INCLUDE[ssDE](../../includes/ssde-md.md)] questo campo restituisce sempre NULL.|  
  
## <a name="remarks"></a>Remarks  
 I nomi di database restituiti possono essere utilizzati come parametri nell'istruzione USE per modificare il contesto del database corrente.  
  
 **sp_databases** non ha un equivalente in Open Database Connectivity (ODBC).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CREATE DATABASE, ALTER ANY DATABASE o VIEW ANY DEFINITION ed è necessario disporre dell'autorizzazione di accesso al database. Non è possibile negare l'autorizzazione VIEW ANY DEFINITION.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrata l'esecuzione di `sp_databases`.  
  
```sql  
USE master;  
GO  
EXEC sp_databases;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [HAS_DBACCESS &#40;Transact-SQL&#41;](../../t-sql/functions/has-dbaccess-transact-sql.md)  
  
  
