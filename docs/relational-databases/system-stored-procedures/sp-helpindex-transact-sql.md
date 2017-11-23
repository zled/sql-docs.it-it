---
title: sp_helpindex (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpindex_TSQL
- sp_helpindex
dev_langs: TSQL
helpviewer_keywords: sp_helpindex
ms.assetid: c7f73ba0-ec35-4b10-aa5f-f1487e51fbf7
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 0738707c9fb232d385fb8f192c8347d70073c15b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpindex-transact-sql"></a>sp_helpindex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sugli indici di una tabella o una vista.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpindex [ @objname = ] 'name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@objname=** ] **'***nome***'**  
 Nome completo o non qualificato di una tabella o una vista definita dall'utente. Le virgolette sono necessarie solo se viene specificato un nome di tabella o di vista completo. Nel caso di un nome completo, ovvero contenente un nome di database, il nome del database deve corrispondere a quello del database corrente. *nome* è **nvarchar(776)**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**index_name**|**sysname**|Nome dell'indice.|  
|**index_description**|**varchar(210)**|Descrizione dell'indice in cui viene indicato anche il filegroup di appartenenza.|  
|**index_keys**|**nvarchar(2078)**|Colonne della tabella o della vista in base a cui è stato compilato l'indice.|  
  
 Nel set di risultati le colonne indicizzate in ordine decrescente vengono contrassegnate con un segno meno (-) dopo il nome. Per le colonne indicizzate in ordine crescente (impostazione predefinita) viene visualizzato solo il nome.  
  
## <a name="remarks"></a>Osservazioni  
 Se gli indici sono stati impostati utilizzando l'opzione NORECOMPUTE dell'istruzione UPDATE STATISTICS, queste informazioni vengono specificate nel **index_description** colonna.  
  
 **sp_helpindex** espone solo le colonne di indice ordinabili, pertanto non espone informazioni sugli indici XML o spaziali.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sui tipi di indice della tabella `Customer`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpindex N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
  
  
